# Adding local machine puclic SSH to GitHub

### Create a SSH Key

In below three method, Choose one command which suits your requirement to create a SSH Key

**Method 1** generating key-gen using default using rsa
```bash
ssh-keygen 
```

**Method 2**
For UEFI System
```bash
$ ssh-keygen -t ed25519 -C "your_email@example.com"
```

**Method 3**
For legacy system
```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

In this command, it will ask the filename to save, press enter to go with default or if you know more about ssh then try to change 
your file and don't forget to protect your private key

<hr>

### Setting up SSH key for GitHub
First add ssh to ssh-agent

Start the ssh-agent in the background
```bash
eval "$(ssh-agent -s)"
```
For root user add `sudo -s -H` before ssh-agent


Now add private key to ssh-agent
```bash
ssh-add ~/.ssh/id_ed25519
```
Go to `~/.ssh/` and copy the file content of `id_rsa.pub` or `id_ed25519.pub` or `custom_name.pub`
```bash
cd ~/.ssh
```
---
### Copying manually

|id-rsa | id_ed25519 | Custom id name |
|------|-------|-------|
|`cat id_rsa.pub`|`cat id_ed25519.pub`| `cat custom_name.pub` |

Now copy the code returned below

### Copying using xclip

First check you have xclip
```bash
xclip -version
```

If it says command not found then install it using pacman
```bash
pacman -S xclip
```

Now got to `.ssh` directory
```bash
cd ~/.ssh/
```

copy using xclip
|id_rsa | id_ed25519 | Custom id name |
|------|-------|-------|
|`xclip -selction clipboard < id_rsa.pub`|`xclip -selction clipboard < id_ed25519.pub`| `xclip -selction clipboard < custom_name.pub` |
---
### Add public key on github
Open github and click on settings

![open settings](https://docs.github.com/assets/images/help/settings/userbar-account-settings.png)

In the side bar, click SSH and GPG keys

![Open SSH in Side bar](https://docs.github.com/assets/images/help/settings/settings-sidebar-ssh-keys.png)

Now click new SSH and Add key 

![add new key](https://docs.github.com/assets/images/help/settings/ssh-add-ssh-key.png)

Add any title for you key and then paste the code in key input box

![](https://docs.github.com/assets/images/help/settings/ssh-key-paste.png)

now add click on `Add SSH Key` and give your github password! Now you can push and pull files without typing any password :)

**Make sure that you copy the SSH when you clone some repo**
---
### Setting up email and password for git 
You may get error, if you haven't added email and name in git config file. Run these two commands to solve this issue
```
git config --global user.email "you@example.com"
```
```
git config --global user.name "you name"
```
