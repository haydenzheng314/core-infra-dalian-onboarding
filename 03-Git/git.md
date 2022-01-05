# 1. Git :

## Install Git on Xubuntu.

Launch terminator.

```
sudo apt install git
sudo apt install gik git-gui
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

Usually we have two ways to clone a repo:

Way 1: **REC**

1. In terminal, create the directory, make it a repository. 
```
    mkdir /home/repo/liferay-portal
    cd /home/repo/liferay-portal
    git init
```

2. Copy liferay-portal repo from hard disk to /home/repo/liferay-portal

3. In your forked repo on GitHub, click **code**, copy the SSH URL.

4. Back to terminal, change the origin from others' to yours by typing:
```
    git remote set-url origin ${SSH URL}
```



Way 2:

1. In your forked repo on GitHub, click **code**, copy the SSH URL.  
2. In terminal, type:  

```
    cd /home/repo
    git clone {SSH URL}
```

3. Repo cloned by this way only has origin connections. To add the upstream, type:

```
    cd liferay-portal
    git remote add upstream git@github.com:liferay-core-infra/liferay-portal.git
```

Once you complete the clone, here are two commands used to check:

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