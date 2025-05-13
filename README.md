# OS Configuration (Windows | Ubuntu | MacOS)

Ubuntu dev environment setup [Link 1](https://gist.github.com/BeKnowDo/f4add66cc28083783e003785f86d7817), [Link 2](https://dev.to/erikaheidi/setting-up-an-ubuntu-2204-workstation-for-software-development-and-content-creation-1ddj)

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
[OBS](https://obsproject.com/download), [BG remove plugin](https://github.com/royshil/obs-backgroundremoval) | [See video](https://www.youtube.com/watch?v=8798QbmWp08&ab_channel=MichaelFeyrerJr.)



### Install Apps

>Don't install **Node.js** directly. Use **nvm** to install **Node.js** multiple version.
>
>See details about [**nvm Usage**](https://github.com/coreybutler/nvm-windows)
>

1. Download nvm latest version for windows10, 11 [from here](https://github.com/coreybutler/nvm-windows/releases)
2. Right click and open "Run as administrator"
3. Install it as default and check "nvm-directory" and "nvm-symlink-directory" successfully added.
4. Open `cmd` windows-terminal with run as administrator **N.B. Make sure its run as Administrator**
5. Run command `nvm install specific_version_number_of_node`, example: `nvm install 16.17.0`
6. Then run `nvm use 16.17.0`

You can check `npm` status by `npm --version` and install **Yarn** by `npm`. Type `npm install --global yarn` and check status `yarn --version`.

### Apps List

Name | Purpose
------------ | -------------
[Visual Studio Code](https://visualstudio.microsoft.com/), [Jetbrians Product](https://www.jetbrains.com/products/) | Text Editor
[Google Chrome](https://www.google.com/chrome/fast-and-secure/), [Firefox](https://www.mozilla.org/en-US/firefox/products/) | Web Browser
[Rectangle](https://rectangleapp.com/) | Window Resizing
[DrawBoardPDF](), [CrystalDiskInfo]() | Some Helpfull Tools
[Discord](https://discord.com/), [Slack](https://slack.com/), [Skype](https://skype.com/) | Communication Tools
[Photopea](https://www.photopea.com/), [Gravit Designer](https://www.designer.io/en/), [Figma](https://www.figma.com/), [Adobe XD](https://www.adobe.com/products/xd.html) | Online Design Tool
[Photoshop CC](https://www.adobe.com/products/photoshop.html), [Illustrator CC](https://www.adobe.com/products/illustrator.html) | Deep Design Tool
[Postman](https://www.postman.com/) | API Tool
[ngRok](https://ngrok.com/) | Make Public URL (Live Server)
[BrowserStack](https://www.browserstack.com/) | Apps & Browser (Testing Tool)

### Development Config List

Name | Purpose
------------ | -------------
[Terminal zsh](https://github.com/ohmyzsh/ohmyzsh) | Config theme: 'agnoster', Install icon: if terminal icon not found
ZSH Plugin | Plugin: (git, autocomplete, asdf)
asdf install | Version Management Tool for all (Ruby, Java, Node.js etc.)
`asdf` important commands | version: `asdf version`, details-info: `asdf info`, current-status: `asdf current`, show-all-installed-list: `asdf list`
`java` install | [Link here](./JAVA.md)

## SSH Key Config and Git with Github (Multiple manage from 1 pc)
- Generate two SSH keys (if you haven't already): If you have two different SSH keys, skip this step. Otherwise, you can generate another key with the following command:
```bash
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"

```
When prompted for a file to save the key, use a unique name (e.g., `~/.ssh/id_rsa_personal` and `~/.ssh/id_rsa_work`).
- Add both SSH keys to your SSH agent
```bash
ssh-add ~/.ssh/id_rsa_personal
ssh-add ~/.ssh/id_rsa_work

```
- List loaded keys to verify:
```bash
ssh-add -l

```
- Start the agent:
```bash
eval "$(ssh-agent -s)"

```
- Create or modify the SSH config file: Open the `~/.ssh/config` file in a text editor (create it if it doesn't exist):
```bash
nano ~/.ssh/config

```
- Add your configuration for both keys: Add the following configuration to the `~/.ssh/config` file:
```bash
# Personal GitHub account
Host github-personal
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_rsa_personal
  IdentitiesOnly yes

# Work GitHub account
Host github-work
  HostName github.com
  User git
  IdentityFile ~/.ssh/id_rsa_work
  IdentitiesOnly yes

```
This configuration sets up aliases (`github-personal` and `github-work`) to switch between your two keys.
- Clone repositories using the correct alias: When cloning a repository, use the corresponding alias for the key you want to use.
```bash
#personal and work
git clone git@github-personal:username/repo.git
git clone git@github-work:username/repo.git

```
**When pushing or pulling code, Git will automatically use the correct SSH key based on the repository URL you cloned.**
### N.B >> Additional Tips
If you’ve already cloned a repository without specifying the alias, you can update the remote URL using:
- First check current-remote-origin-status
```bash
git remote show origin
```
Result(like):
```shell
* remote origin
  Fetch URL: git@github.com:plabon-asad/cinnabar-shop-api.git
  Push  URL: git@github.com:plabon-asad/cinnabar-shop-api.git
  HEAD branch: master
  Remote branch:
    master tracked
  Local branch configured for 'git pull':
    master merges with remote master
  Local ref configured for 'git push':
    master pushes to master (fast-forwardable)
```
- Update the remote URL using
```bash
git remote set-url origin git@github-personal:username/personal-repo.git
```

## [SSH and Git Config](https://dev.to/bdbch/setting-up-ssh-and-git-on-windows-10-2khk)

Test your SSH key connection `ssh -T git@github.com`, [Link here](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/testing-your-ssh-connection)

Open **Windows terminal** to Create a **SSH Key and config key with Github** account.
```
ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```
This generates a new private SSH key with rsa encryption and **4096 bits**. It also generates a public key from the secret key which you can share around.
<br>🔰 N.B. Multiple ssh key config, [Link here](https://www.youtube.com/watch?v=pE3EuiyShoM)

#### File & Folder Access by Terminal
| Command  |  Description |
|---|---|
|  `pwd` | Current directory path  |
|  `cd` | Change directory path  |
|  `ls -l ~/.ssh` | See (Read/Write) mode of that folders All files  |
|  `cat ~/.ssh/id_rsa.pub` | This `cat` command concate all text from on that file  |
|  `rm targeted_file` | Targeted file will be delete  |
|  `rm targeted_file*` | File name matched with first by`targeted_file` and then all file on that named will be delete  |


#### Register your SSH Key on Github
```
type C:\Users\your_pc_user_name\.ssh\id_rsa.pub
```
In terminal show you **ssh-key** copy it and add this key on your **Github, Bitbucket, etc.**

## Adding or changing a passphrase
You can change the passphrase for an existing private key without regenerating the keypair by typing the following command:
```
$ ssh-keygen -p -f ~/.ssh/id_ed25519
> Enter old passphrase: [Type old passphrase]
> Key has comment 'your_email@example.com'
> Enter new passphrase (empty for no passphrase): [Type new passphrase]
> Enter same passphrase again: [Repeat the new passphrase]
> Your identification has been saved with the new passphrase.
```

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
[Angular](https://angular.io/cli) | Angular `npm install -g @angular/cli`. On Windows client computers, the execution of PowerShell scripts is disabled by default. To allow the execution of PowerShell scripts, which is needed for npm global binaries, you must set the following `Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned` [see here](https://angular.io/guide/setup-local)
[Ionic](https://ionicframework.com/docs/v3/developer-resources/platform-setup/windows-setup.html) | Ionic
[Cordova](https://www.npmjs.com/package/cordova) | Cordova `npm install -g cordova`
[Rails](https://gorails.com/setup/windows/10) | Ruby and ROR

## Shell config
 - How do I know which shell using my `Linux` or `Mac` pc: `echo $SHELL`
 - Go to directory and show hidden file for `Linux`- "Cntrl + h", `Mac`- "Command + Shift + ."
 - Open it by text editor, edit it and save it. 
 - After that reload this by terminal: `source ~/.zshrc` - (zshrc means which bash_profile are using)

## Environment Variable Set
Here you will get some more helpful info, [Link...](https://developer.android.com/tools/variables#set)

## Linux setup by WSL in Windows-11

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
`explorer.exe .` | See full-path of WSL/Windows11 by terminal. Open terminal which one you want to see and run command, a folder will open with required path.

Basic commands details [link](https://docs.microsoft.com/en-us/windows/wsl/basic-commands) here you can see and learn also more.

<br>**📍To navigate to any-drive in bash on WSL2-Ubuntu18.04!** [Link here](https://askubuntu.com/questions/831361/can-i-change-directory-to-a-windows-drive-in-ubuntu-bash-on-wsl)

WSL stores your Windows drives in the `/mnt` folder, with the name of the drive as a subfolder. For example your `C:\` drive will be present at `/mnt/c/` for you to use. Keeping this in mind, you can swap to your specific folder like so `cd /mnt/e/username/folder1/folder2`

<br>**📍Multiple terminal open in WSL2-Ubuntu18.04!** [Link here](https://askubuntu.com/questions/1074283/multiple-terminal-windows-in-windows-ubuntu)

### Setup development environment

Command | Description and Link
------------ | -------------
`sudo apt-get update` | Update Ubuntu
`sudo apt-get install git-core curl zlib1g-dev build-essential libssl-dev libreadline-dev libyaml-dev libsqlite3-dev sqlite3 libxml2-dev libxslt1-dev libcurl4-openssl-dev software-properties-common libffi-dev` | First some dependencies for Ruby

### Install `rvm` - [Help link](https://github.com/rvm/ubuntu_rvm)

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

### Install Ruby
Some necessary command of `rvm`. To see available version from online`rvm list known`, installed list of ruby`rvm list`, current using version`rvm current`, install latest version of ruby `rvm install ruby`, installed specific version of ruby `rvm install ruby_version_number` like `rvm install 2.3.1`

⛑️ If broken any installation of ruby for week network or any other reasons, you can fix it by ***reinstallation*** by `rvm reinstall ruby_version_number`. Before it you should restart the mechine.


### Install Node.js by NVM - [Help Link](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-18-04)

Before piping the command through to bash, it is always a good idea to audit the script to make sure it isn’t doing anything you don’t agree with. You can do that by removing the | bash segment at the end of the curl command
``` 
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh
```

Review the output and make sure you are comfortable with the changes it is making. Once you’re satisfied, run the same command with | bash appended at the end. The URL you use will change depending on the latest version of NVM, but as of right now, the script can be downloaded and executed by running the following
``` 
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash
```

This installs the nvm script to your user account. In order to use it, first source the .bashrc file
``` 
source ~/.bashrc
```
First, ask nvm what versions of Node are available
``` 
nvm ls-remote
```

Install a specific version of node
```
nvm install v16.13.1
```

After done check status `node -v`

Install a specific version of Rails `gem install rails -v version_number`
```
gem install rails -v 7.0.2.4
```

### Install Mysql, Apache, PhpMyadmin in WSL2-Ubuntu18.04! [Link here](https://geekrewind.com/how-to-install-phpmyadmin-on-windows-11-wsl/)
 1. Install Apache HTTP Server
 2. Install MariaDB Database Server
 3. PHP and Related Modules
 4. Install phpMyAdmin
<br> 

1. To install Apache on Ubuntu `sudo apt install apache2`. After done, use command to stop, start and restrat **Apache2**: `sudo service apache2 stop`, `sudo service apache2 start`, and `sudo service apache2 restart`.
2. To install MariaDB, run the commands below: `sudo apt-get install mariadb-server mariadb-client`. After installing MariaDB, the commands below can be used to stop, start and restart MariaDB services `sudo service mysql stop`, `sudo service mysql start`, and `sudo service mysql restart`.<br><br>
Next, run the commands below to secure the database server with a root password if you were not prompted to do so during the installation 
```sudo mysql_secure_installation```
  When prompted, answer the questions below by following the guide.
  - Enter current password for root (enter for none): Just press the Enter
  - Set root password? [Y/n]: Y
  - New password: Enter password
  - Re-enter new password: Repeat password
  - Remove anonymous users? [Y/n]: Y
  - Disallow root login remotely? [Y/n]: Y
  - Remove test database and access to it? [Y/n]:  Y
  - Reload privilege tables now? [Y/n]:  Y <br>
 To verify and validate that MariaDB is installed and working, login to the database console using the commands below: `sudo mysql -u root -p`
3. PHP is a general-purpose scripting language that enables the LAMP and LEMP stack and is required by phpMyAdmin.To install PHP and recommended modules, run the commands below: `sudo apt install php libapache2-mod-php php-common php-mysql php-gmp php-curl php-intl php7.2-mbstring php-xmlrpc php-gd php-xml php-cli php-zip`<br>
To verify php version write: `php -v`
4. Now that you have installed Apache, MariaDB and PHP, run the commands below to install phpMyAdmin `sudo apt install phpmyadmin`.<br>
When prompted to choose the webserver, select apache2 and continue. When prompted again to allow debconfig-common to install a database and configure select Yes.

Enter a password and confirm for phpMyAdmin to register with the database, then select OK and complete the installation. MySQL and MariaDB come with a feature that provides root authentication via a **auth_socket plugin**.<br><br>This plugin authenticates users who connect from the localhost via socket file without prompting or using a password. If you attempt to logon to phpMyAdmin with the MariaDB root account, you won’t be allowed.<br><br>If you wish to use the root account to logon to phpMyAdmin, then use the steps below. To fix that, you’ll need to change the default authentication mechanism from auth_socket to mysql_native_password.<br><br>Login back into MariaDB console `sudo mysql`.

Then run the commands below to change to disable **mysql_native_password** module.
```
USE mysql;
UPDATE user SET plugin='' WHERE user ='root';
```
The save your changes and exit:
``` 
FLUSH PRIVILEGES;
EXIT;
```
Restart **Apache** and browse to phpMyAdmin web portal using the URL: `http://localhost/phpmyadmin`

### Install PG in WSL2-Ubuntu18.04!

1. Open your WSL2 Ubuntu terminal and run `sudo apt-get update`
2. Run `sudo apt install postgresql postgresql-contrib`
3. Confirm installation by check version `psql --version`
4. Check status, start, stop and restart pg server by command `sudo service postgresql status`, `sudo service postgresql start`, `sudo service postgresql stop`, and `sudo service postgresql restart`

#### PG config
1. Login to PG Console `sudo -u postgres psql`
2. Show DB: `\l`, create DB: `CREATE DATABASE db_name;`, delete DB: `DROP DATABASE db_name;`
3. Create a Superuser and set grant access:
```
CREATE USER user_name WITH PASSWORD 'password';
ALTER USER user_name WITH SUPERUSER;
GRANT ALL PRIVILEGES ON DATABASE db_name TO user_name;

```
4. Show DB users: `SELECT usename FROM pg_catalog.pg_user;`, delete user: `DROP USER user_name`
5. List Users with Roles: `SELECT rolname, rolsuper, rolinherit, rolcreaterole, rolcreatedb, rolcanlogin, rolreplication, rolbypassrls
FROM pg_catalog.pg_roles;
`
6. Check all DB `\l` and exit console `\q`

### Install Redis by WSL2 - [Link](https://redis.io/docs/getting-started/installation/install-redis-on-windows/)
1. To install recent stable versions of Redis from the official packages. Add the repository to the apt index, update it, and then install.
```
curl -fsSL https://packages.redis.io/gpg | sudo gpg --dearmor -o /usr/share/keyrings/redis-archive-keyring.gpg

```
```
echo "deb [signed-by=/usr/share/keyrings/redis-archive-keyring.gpg] https://packages.redis.io/deb $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/redis.list

```
```
sudo apt-get update
sudo apt-get install redis

```
2. After install check installed version `redis-server -v`
3. Update `redis.conf` file, Run the folowing command to open `redis.conf` file: `sudo nano /etc/redis/redis.conf`. Find `supervised no` line and change to `supervised systemd`, save and exit. Since Ubuntu uses the systemd init system. 
4. Check Redis status, start, stop and restart command `sudo service redis-server status/start/stop/restart`


### Swap space Problem (Ubuntu 22.04LTS)
#### Question to ChatGPT:
`I am a full-stack developer, I worked on Ruby on Rails, Ionic, Android, Java and so many languages. So which amount should I config with swap now for smooth development perform in ubuntu 22.04, please show me config step by step.`

#### Answer from ChatGPT:
`To ensure smooth development performance on your Ubuntu 22.04 system, especially with the diverse range of tools and languages you work with, I recommend setting your swap space to at least 16GB. This will provide sufficient virtual memory to handle the demands of development environments and multiple applications running simultaneously.`

#### Step-by-Step Instructions: 
```
# Disable any existing swap space
sudo swapoff -a

# Remove the old swap file if it exists
sudo rm /swapfile

# Create a new swap file with a size of 64GB
sudo dd if=/dev/zero of=/swapfile bs=1G count=64

# Set the correct permissions
sudo chmod 600 /swapfile

# Set up the file as a swap space
sudo mkswap /swapfile

# Enable the swap file
sudo swapon /swapfile

# Verify the new swap space
sudo swapon --show

# Edit /etc/fstab to make the swap file permanent
sudo nano /etc/fstab

# Add the following line to /etc/fstab
/swapfile none swap sw 0 0

# Verification
free -h

```

### Ubuntu install and uninstalled study:
```sh
// All installed app
sudo apt list --installed

// Show upgradable list of apps
sudo apt list --upgradable

// Update and upgrade installed app
sudo apt update
sudo apt upgrade

// Remove or uninstall an app
sudo apt remove name_app1 name_app2
``` 


