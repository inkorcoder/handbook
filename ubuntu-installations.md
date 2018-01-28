# Ubuntu :: Installations

## Google Chrome
- [Download here](https://www.google.com/chrome/browser/desktop/index.html)
- `ls` - find out chrome package name (in my case: google-chrome-stable.deb)
- `sudo dpkg -i google-chrome-stable.deb` - install. After that you can see dependencies error in terminal
- `sudo apt-get install -f` - fix the problem

## Telegram
#### 14.04, 17.10 (works for me)
- `sudo add-apt-repository ppa:atareao/telegram` - add a repository
- `sudo apt-get update` - update packages
- `sudo apt-get install telegram` - install it
#### 16.04
- download [here](https://desktop.telegram.org/)
- unzip by `tar -xvf tsetup.1.2.6.tar.xz`
- and install by `cd Telegram && ./Telegram`

## Aliases
First of all, open your `.bashrc`. You can do this in few ways:
- `gedit ~/.bashrc` - by default `gedit` is a text editor in ubuntu
- `nano ~/.bashrc` - practicaly every distro has `nano` editor
- `subl ~/.bashrc` - if you already have (Sublime Text)[http://www.sublimetext.com/] installed

Next, paste this code or create your own aliases
```
alias u='sudo apt-get update'
alias i='sudo apt-get install'
alias f='sudo apt-get install -f'
alias ar='sudo apt-get autoremove'
alias ac='sudo apt-get autoclean'
alias di='sudo dpkg -i'
 
alias s30='sudo shutdown -h 30'
alias s60='sudo shutdown -h 60'
alias s90='sudo shutdown -h 90'
alias s120='sudo shutdown -h 120'
alias s150='sudo shutdown -h 150'
 
alias nf='cd node'
alias wf='cd node/work'
```

and after that apply the changes by `source ~/.bashrc` command

## My weather indicator
- `sudo add-apt-repository ppa:atareao/atareao` - add a repo
- `sudo apt-get update && sudo apt-get install my-weather-indicator` - update packages and install indicator

## Indicator multiload
It already exist in repos, so you can simply install it:
- `sudo apt-get install indicator-multiload`
In LXDE this indicator fails to render if bar width larger than 20px

## Automount your hard drive partitions
By the default ubuntu mount your non-linux partitions temporary with strange names sometimes (cyrrilic for example): /media/inkor/1A70413C7041203D
If you use this partitions in your audio player, after rebooting the system it becomes to crash because of non-existed files
To set up automount follow this commands:
- `sudo blkid` - find out your partitions names and labels
- `sudo mkdir /mnt/<folder>` - create folders for further mounting (for each drive). In my case it will be `sudo mkdir /mnt/sys` for Drive C:/ and `sudo mkdir /mnt/media` for Drive D:/
- `sudo gedit /etc/fstab` - open config
- `UUID="56082E18082DF81F" /mnt/sys ntfs rw,nls=utf8,gid=plugdev,umask=0002 0 0` - paste your entry point, set `UUID` for drive you need
- `sudo umount -a` - unmount all partitions
- `sudo mount -a` - mount all partitions but with new folders
now you can go to /mnt/ and find your drives (sys, media in my case) and create links for it in your file manager
