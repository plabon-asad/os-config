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

