# Git :

1. Install Git on Xubuntu.

    Launch terminator.

        sudo apt update
        sudo apt install git
        sudo apt install gik git-gui

    After installation compeleted, you can verify it by typing: `git --version`

2. Set up your name and email

        git config --global user.name "your.name"  
        git config --global user.email your.name@liferay.com

    This will change the values in `~/.gitconfig` or `~/.config/git/config`, which is specific to the current user. 

    >If you want it to be available for every user in your system, use --system instead of --global.  
    >Or you only want it to be available for the current repository, use --local.


# Git repository: 

A Git repository is a virtual storage of your project. Usually we put git repositories in /home/repo, launch terminal to create it and set its ownership.

        sudo mkdir /home/repo
        sudo chown name:name /home/repo

There are three copies of repositories (called repo for short) that concern you:

1. In GitHub, open [liferay-portal](https://github.com/liferay/liferay-portal) repo. This is the remote parent repo called _upstream_.

2. Click **Fork** at the top-right corner, select your own account. The page will jump to your-name/liferay-portal, which is your own remote repo called _origin_.

3. After forking, you need to clone the repo to your laptop as a local repo. Usually we have two ways to clone:

- Way 1: **REC**

    1). Launch terminal under /home/repo , create a directory named **liferay-portal**.

        mkdir liferay-portal
        cd liferay-portal

    2). Type `git init` to make the directory a repository.

    3). Copy liferay-portal repo from hard disk to /liferay-portal

    4). Type `git remote -v`, it shows origin and upstream connections with the URL of each one. The upstream points to liferay repo, keep it as is. The origin has to be changed to point to yours.

    5). In your repo on GitHub, click **code**, copy the SSH URL. Head over to terminal, type:

        git remote set-url origin ${SSH URL}

- Way 2: 

    If the network is great, you can try this way with less steps.

    1). In your repo on GitHub, click **code**, copy the SSH URL.  
    2). In file system, launch terminal under /home/repo, type:  

        git clone {SSH URL}

    3). Repo cloned by this way only has origin, so add the upstream.

        cd /liferay-portal
        git remote add upstream git@github.com:liferay-core-infra/liferay-portal.git

Once you complete the clone, type `git status` in terminal under /liferay-portal to display the state of the working directory and the staging area.

# GitHub CLI

GitHub CLI is the official GitHub command line, install it by follows.

1. Add a reference to the package repository.

        sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-key C99B11DEB97541F0
        sudo apt-add-repository https://cli.github.com/packages

2. Install GitHub CLI

        sudo apt install gh