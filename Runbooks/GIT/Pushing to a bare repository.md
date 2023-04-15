# How to push to a local git repository 
## But why?
Well in my case I wanted to use obsidian's git plugin to make automatic backups. I could have used our github enterprise but since we have a NAS, and can use that to share files with colleagues I decided to make a repo on the nas instead.

This will also work for a git repository within google drive, dropbox, mega.nz or any other cloud provider that allows you to access the files from your operating system's file explorer (windows explorder on windows, finder on mac.... *dolphin for kde, nautilus for ubuntu... etc...*)

While the NAS isn't 'local', it is local from the perspective of git since a NAS gets mounted to the file system.


## Step 1: Create a Bare Repository

```bash
git init --bare
```

This essentially creates a git repository that doesn't have a working tree, meaning its (almost) just the contents of the .git folder. With a bare git repository you are unable to make changes and instead are meant to push/pull from it. If you don't use a bare repository git will complain when you try to make a push to the local directory.

## Step 2: Add remote

```bash
git remote add origin /path/to/bare/repo
```

If you have an origin already, it might make sense to use local as your name and then you can use `git push all` to push to all remotes (origin & local) if not, I'd recommend calling it origin as thats the default name.

If you're on **windows**, while you may normally be used to doing `C:\` for git you can use `/c/path/to/folder` to make things easier. Also this is the format thats returned by the `pwd` program that comes with git bash when you install it.

## Step 3: Push as normal

```bash
# if you didn't make any commits, make one
git add .
git commit -m "initial commit"
# push
git push
```

## Step 4: Profit
You now have a remote local repository/

If you're also using this with Obsidian's git plugin, I'd recommend a high number between updates or your bare repository will get very large very fast. If you want to remove old commits, you can do this with rebase.

> Make sure to do this from the repo inside the obsidian vault.

```bash
git rebase -i HEAD~4
```

Since you're rewriting history you'll need to then force push, so you might want to do a manual commit and push here.