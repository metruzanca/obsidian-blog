## Install fish repository in ubuntu

sudo apt-add-repository ppa:fish-shell/release-3;

sudo apt-get update && sudo apt-get upgrade;

  

## Install fish shell

sudo apt-get install fish;

  
  

## Make fish shell as default shell

  

## Detect if running in WSL or linux/macos

if [[ $(grep microsoft /proc/version) ]];

WSL doesn't want sudo
```
chsh -s /usr/local/bin/fish;
```  

## Install oh my fish

curl https://raw.githubusercontent.com/oh-my-fish/oh-my-fish/master/bin/install | fish