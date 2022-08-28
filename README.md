# Operating System Configuration

Setting up a Windows10 for Development

## Getting Started

In [windows-10](https://www.microsoft.com/en-us/software-download/windows10) at first I got some issues there are - 

1. Wrong keyword typing in "Keyboard"
2. Driver install **Touchpad , Graphics, Audio, etc.** Its depends on what types of Brand Laptop/PC you are using. Just google it by your Brand name and install by Brand official tools like [Lenovo](https://pcsupport.lenovo.com/bd/en/products/laptops-and-netbooks/300-series/320-15isk/downloads/automatic-driver-update)
3. File explorer tab install. [See how?](https://www.youtube.com/watch?v=Dt5JpnF4hW0)

Problem | Solution
------------ | -------------
Keyboard typing | [Wrong keyword typing in "Keyboard"](https://www.youtube.com/watch?v=cT_6uDoq1QI)
Driver Install | [Lenovo](https://pcsupport.lenovo.com/bd/en/products/laptops-and-netbooks/300-series/320-15isk/downloads/automatic-driver-update)
File explorer tab install | [Download QTTabBar](http://qttabbar.wikidot.com/)

## Windows-10: Some Essiential Apps 

Name | Link
------------ | -------------
[Net Speed Monitor](https://netspeedmonitor.net/download/) | [See video](https://www.youtube.com/watch?v=haLNdy2ozrc)



### Install Apps

>Don't install **Node.js** directly. 
>
>Use [**nvm**](https://github.com/coreybutler/nvm-windows/releases/download/1.1.7/nvm-setup.zip) to install **Node.js** for any version install.
>
>See details about [**nvm Usage**](https://github.com/coreybutler/nvm-windows)


### Apps List

Name | Purpose
------------ | -------------
[Visual Studio Code](https://visualstudio.microsoft.com/), [Jetbrians Product](https://www.jetbrains.com/products/) | Text Editor
[Google Chrome](https://www.google.com/chrome/fast-and-secure/), [Firefox](https://www.mozilla.org/en-US/firefox/products/) | Web Browser
[Rectangle](https://rectangleapp.com/) | Window Resizing
[Discord](https://discord.com/), [Slack](https://slack.com/), [Skype](https://skype.com/) | Communication Tools
[Photopea](https://www.photopea.com/), [Gravit Designer](https://www.designer.io/en/), [Figma](https://www.figma.com/), [Adobe XD](https://www.adobe.com/products/xd.html) | Online Design Tool
[Photoshop CC](https://www.adobe.com/products/photoshop.html), [Illustrator CC](https://www.adobe.com/products/illustrator.html) | Deep Design Tool
[Postman](https://www.postman.com/) | API Tool
[ngRok](https://ngrok.com/) | Make Public URL (Live Server)
[BrowserStack](https://www.browserstack.com/) | Apps & Browser (Testing Tool)

## [SSH and Git Config](https://dev.to/bdbch/setting-up-ssh-and-git-on-windows-10-2khk)

Open **Windows terminal** to Create a **SSH Key and config key with Github** account.
```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
This generates a new private SSH key with rsa encryption and **4096 bits**. It also generates a public key from the secret key which you can share around.

#### Register your SSH Key on Github
```
type C:\Users\your_pc_user_name\.ssh\id_rsa.pub
```
In terminal show you **ssh-key** copy it and add this key on your **Github, Bitbucket, etc.**

### Globally git config

[Download Git](https://git-scm.com/download/win) and **Install** it.
After install open **Git-bash** terminal and type

```
git config --global user.name "your_github_user_name"

git config --global user.email "your_github_email"
```
Congratulations! you have successfully config **git**.

### Development config

Link | Name
------------ | -------------
[Angular](https://angular.io/cli) | Angular `npm install -g @angular/cli`
[Ionic](https://ionicframework.com/docs/v3/developer-resources/platform-setup/windows-setup.html) | Ionic
[Cordova](https://www.npmjs.com/package/cordova) | Cordova `npm install -g cordova`
[Rails](https://gorails.com/setup/windows/10) | Ruby and ROR

## Getting Started with Windows 11

Trying to config [Ubuntu](https://ubuntu.com/) without leaving Winodows by [WSL(Windows Subsystem for Linux)](https://ubuntu.com/wsl)

### Prerequisites
There are a few things you should know in advance before you start playing around with WSL.
- `Turn Windows features on or off` by search Windows bar
- Enables the optional `WSL`, `Virtual Machine Platform`, `Hyper-V` , `Virtual Mechine Platform`, `Windows Sandbox` components by checked it and need to restart your mechine.
- Downloads and installs the latest Linux kernel
- Sets WSL 2 as the default
- Downloads and installs the Ubuntu Linux distribution (reboot may be required)

Open cmd terminal for use these commands step by step.
### Basic commands for WSL
Command | Description and Link
------------ | -------------
`wsl --status` | Check WSL status.
`wsl --install` | Install WSL and the Ubuntu distribution of Linux.
`wsl --install --distribution <Distribution Name>` | Install a specific Linux distribution
`wsl --install --distribution <Distribution Name>` | Designate a distribution of Linux for installation besides the default (Ubuntu) by replacing `<Distribution Name>` with the name of the distribution. This command can also be entered as: `wsl -d <Distribution Name>`.
`wsl --list --online` or `wsl -l -o` | List available Linux distributions at online.
`wsl --list --verbose` or `wsl -l -v` | See a list of the Linux distributions installed on your Windows machine, including the state (whether the distribution is running or stopped) and the version of WSL running the distribution (WSL 1 or WSL 2). Comparing WSL 1 and WSL 2. Additional options that can be used with the list command include: `--all` to list all distributions, `--running` to list only distributions that are currently running, or `--quiet` to only show distribution names.
`wsl --set-version <distribution name> <versionNumber>` | To designate the version of WSL (1 or 2) that a Linux distribution is running on, replace `<distribution name>` with the name of the distribution and replace `<versionNumber>` with 1 or 2. Comparing WSL 1 and WSL 2.
`wsl --set-default-version <Version>` | Set default WSL version
`wsl --set-default <Distribution Name>` | Set default Linux distribution
`wsl ~` | Change directory to home

Basic commands details [link](https://docs.microsoft.com/en-us/windows/wsl/basic-commands) here you can see and learn also more.

### Setup development environment

Command | Description and Link
------------ | -------------
`sudo apt-get update` | Update Ubuntu
`sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev software-properties-common libffi-dev` | First some dependencies for Ruby

### Install `rvm`

1. You need ***software-properties-common*** installed in order to add **PPA** repositories.
```
sudo apt-get install software-properties-common
```

2. Add the PPA and install the package
```
sudo apt-add-repository -y ppa:rael-gc/rvm
sudo apt-get update
sudo apt-get install rvm
```

3. Add your user to rvm group ($USER will automatically insert your username)
```
sudo usermod -a -G rvm $USER
```

4. If you cannot force terminal to perform a login, or you're facing `Command 'rvm' not found`, you can run the following command to append it to your `.bashrc`
```
echo 'source "/etc/profile.d/rvm.sh"' >> ~/.bashrc
```

5. Now rebot your terminal and check status by run `rvm -v`


Help key: []()@#$%&*
