# 1. Git :

## Install Git on Xubuntu.

Launch terminator.

```
sudo apt install git
sudo apt install gitk git-gui
```

After installation compeleted, you can verify it by typing: `git --version`

## Set up your name and email

In terminal, type:

```
git config --global user.name "your.name"  
git config --global user.email your.name@liferay.com
```

This will change the values in `~/.gitconfig` or `~/.config/git/config`, which is specific to the current user. 

>If you want it to be available for every user in your system, use --system instead of --global.  
>Or you only want it to be available for the current repository, use --local.

# 2. GitHub SSH Key

Generate a new SSH key and add it to your GitHub account.

Follow the first five steps in: https://docs.github.com/articles/generating-an-ssh-key/

# 3. Git repository: 

A Git repository is a virtual storage of your project. Usually we put it in /home/repo

In terminal, create the directory and set its ownership.

```
sudo mkdir /home/repo
sudo chown name:name /home/repo
```

There are three copies of repositories (called repo for short) that concern you:

- In GitHub, open [liferay-portal](https://github.com/liferay/liferay-portal) repo. This is the remote parent repo called **upstream**.

- Click **Fork** at the top-right corner, select your own account. The page will jump to your-name/liferay-portal, which is your own remote repo called **origin**.

- After forking, you need to clone the repo to your computer as a local repo. 

Considering the size of repo and the network, we usually copy it directly from the USB disk to the computer instead of using `git clone` command.

1. Copy liferay-portal.tar to /home/repo . In terminal, untar it by typing:
```
    cd /home/repo
    tar xvf liferay-portal.tar
```

2. Go to your forked repo on GitHub, click **code**, copy the SSH URL.

3. In terminal, add or change the origin connection:
```
    cd liferay-portal
    git remote add origin ${SSH URL} / git remote set-url origin ${SSH URL}
```
4. Make sure your local repo and origin repo up to date, type:
```
    git pull upstream master
    git push origin master
```

Once you complete, here are two commands used to check:

 `git status` displays the state of the working directory and the staging area.

 `git remote -v` displays origin and upstream connections with the URL of each one. 

# 4. GitHub CLI

GitHub CLI is the official GitHub command line.

Add a reference to the package repository.

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key C99B11DEB97541F0
sudo apt-add-repository https://cli.github.com/packages
```

Install GitHub CLI.

```
sudo apt install gh
```
