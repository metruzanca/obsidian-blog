git@ssh.dev.azure.com:v3/agencywithin/AWPL/poc-fe

## Create GPG Keys
Run this using all the defaults and add a passphrase
```
gpg --full-generate-key 
```

## Export PGP public key
Export the gpg public key to a file somewhere, I like to use `~/.gnupg/keys/` (*you'll need to create this directory*). Exporting to a file allows us to use the gpg key also for ssh.

```
gpg --armor --export <key-id> > ~/.gnupg/keys/brkfst.io-pgp.pub
```

````ad-info
collapse:true
title: List GPG keys
If you need to get key id again, use this
```
gpg --list-keys
```
````

You'll need to send your public gpg key over to [@Jon Lopinot](@Jon%20Lopinot.md) or whoever is doing the setup for you on the repository.
if on a mac, you can simply use
```
cat ~/.gnupg/keys/brkfst.io-pgp.pub | pbcopy
```

## SSH with GPG key

#### 0 - SSH vs GPG keys

If you're unfamiliar with gpg, here's a quick run down of gpg vs ssh keys.

While ssh keys are single keys, gpg keys are actually a collection of keys. A gpg keyring is composed by a main key (the one we previously created) which is responsible for signing and certification. For other purposes (e.g. encryption) you'll need to create a subkey. 

#### 1 - Create the subkey
Enter the gpg cli

```
gpg --expert --edit-key <key-id>
```

Once in the cli, use the `addkey` command and answer the questions as follows
```diff
Please select what kind of key you want:
 (3) DSA (sign only)
 (4) RSA (sign only)
 (5) Elgamal (encrypt only)
 (6) RSA (encrypt only)
 (7) DSA (set your own capabilities)
 (8) RSA (set your own capabilities)
 (10) ECC (sign only)
 (11) ECC (set your own capabilities)
 (12) ECC (encrypt only)
 (13) Existing key
+ Your selection? 8

Possible actions for a RSA key: Sign Encrypt Authenticate
Current allowed actions: Sign Encrypt

 (S) Toggle the sign capability
 (E) Toggle the encrypt capability
 (A) Toggle the authenticate capability
 (Q) Finished

+ Your selection? s
+ Your selection? e
+ Your selection? a

Possible actions for a RSA key: Sign Encrypt Authenticate
Current allowed actions: Authenticate

 (S) Toggle the sign capability
 (E) Toggle the encrypt capability
 (A) Toggle the authenticate capability
 (Q) Finished

+ Your selection? q
RSA keys may be between 1024 and 4096 bits long.
What keysize do you want? (2048)
Requested keysize is 2048 bits
Please specify how long the key should be valid.
 0 = key does not expire
 <n>  = key expires in n days
 <n>w = key expires in n weeks
 <n>m = key expires in n months
 <n>y = key expires in n years
+ Key is valid for? (0)
Key does not expire at all
+ Is this correct? (y/N) y
+ Really create? (y/N) y
```

Then simply run the `quit` command. (Make sure to save our changes with `y`)

#### 2 - Enable ssh within gpg
To enable ssh with the gpg-agent, we'll need to add the `enable-ssh-support` line to `gpg-agent.conf`.

This can easily be done with:
```
echo enable-ssh-support >> ~/.gnupg/gpg-agent.conf
```

#### 3 - Add the ssh key to ssh agent
To avoid having to add the ssh keys with `ssh-add`, you can add the keys to the `sshcontrol` gpg config file
First we need the key's "keygrip", you can find it doing:
```
gpg -K --with-keygrip
```

Then simply add it via:
```
echo <keygrip> >> ~/.gnupg/sshcontrol
```

#### 4 - Setup gpg-agent env vars

Append these lines to whatever your shell rc file is (probably `~/.zshrc`)
```
# GPG-Agent env vars
export SSH_AUTH_SOCK=$(gpgconf --list-dirs agent-ssh-socket)  
gpgconf --launch gpg-agent
```

