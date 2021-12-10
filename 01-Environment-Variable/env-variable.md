# Environment variable

Before any setup, press "Ctrl+Alt+T" to launch terminal.

Type:

```
sudo apt update
```

to download and update the package information from all of the configured sources.

Then type:

```
sudo apt dist-upgrade
```

to run a system upgrade.

## Tools

Usually we put JDK, Ant, Maven in /opt .

In terminal, set the directory ownership.

```
sudo chown username:username /opt
```

`username` is the name of the user you use to log in to the operating system. When IT installs Xubuntu for you, they usually set the username `liferay`.

Create three directories:

```
mkdir /opt/jdk
mkdir -p /opt/tools/apache-ant
mkdir -p /opt/tools/apache-maven
```

### JDK

Get jdk1.8.0-181.tar.gz (version depends), in terminal, go to the directory where the tar.gz file is, and type:

```
tar -xzvf jdk1.8.0-181.tar.gz
mv jdk1.8.0-181 /opt/jdk/
```

to extract JDK and move it to `/opt/jdk`

Then, type the following command to create a symbolic link pointing to the JDK directory。

```
ln -s /opt/jdk/default /opt/jdk/jdk1.8.0_181
```

> It's possible that you need to have multiple versions of JDK on your computer, and switch among them. With this way, you can just remove/recreate links to switch the system-wide JDK, without changing environment variables. We'll mention this later.


### Ant 

Get apache-ant-1.10.11.tar.gz (version depends), extract it and move it to `/opt/tools/apache-ant`

### Maven

Get apache-maven-3.8.2.tar.gz (version depends), extract it and move it to `/opt/tools/apache-maven`

## 2. Configure Environment variables

Copy (Ctrl+C) the environment variables below:

```
JAVA_HOME=/opt/jdk/default
ANT_HOME=/opt/tools/apache-ant
MAVEN_HOME=/opt/tools/apache-maven

ANT_OPTS="-Xmx4096m"

PATH=$JAVA_HOME/bin:$ANT_HOME/bin:$MAVEN_HOME/bin:$PATH

export JAVA_HOME ANT_HOME MAVEN_HOME PATH ANT_OPTS
```

>Note: If your directory path is different, please make the corresponding change in environment variables.

In terminal, type:

```
sudo apt install vim
vim ~/.profile
```

When you launch Vim, you enter the command mode. Although Vim shows the contents of ~/.profile, you can not edit the content yet.

> In Vim:
> - Press "i" to enter the insert mode to edit the content;
> - Press "Esc" to exit the insert mode (switch back to command mode)

Now press "i" to enter the insert mode, and use arrow keys (↑ ↓ ← →) to move the cursor. 

Press "Ctrl+Shift+V" to paste environment variables to the end of the file.

Then press "Esc", type `:wq` to save and quit.

In terminal, activate the environment variable changes:

```
source ~/.profile
```

> `source` will only take effect in the current terminal window. To apply the environment variable changes to the whole system, restart your computer.