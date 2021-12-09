# Environment variable

Before any setup, press "Ctrl+Alt+T" to launch terminal, type:

        sudo apt update

To download and update the package information from all of the configured sources.

## 1. Tools

Usually we put JDK, Ant, Maven in /opt .

Launch terminal, set the directory ownership.

```
sudo chown name:name /opt
```

Create three directories:

```
mkdir /opt/jdk
mkdir -p /opt/tools/apache-ant
mkdir -p /opt/tools/apache-maven
```

### 1-1. JDK

1. Get jdk1.8.0-181.tar.gz (version depends), extract it under /opt/jdk

2. In terminal, create a symbolic link pointing to the JDK directory。

        ln -s /opt/jdk/default /opt/jdk/jdk1.8.0_181

>With this way, if you have multiple versions of tools or need to upgrade it, you can just remove/recreate links, without changing environment variables. We'll mention this later.


### 1-2. Ant 

Get apache-ant-1.10.11.tar.gz (version depends), extract it under /opt/tools/apache-ant


### 1-3. Maven

Get apache-maven-3.8.2.tar.gz (version depends), extract it under /opt/tools/apache-maven


## 2. Configure Environment variables

1. Copy environment variables below:

        JAVA_HOME=/opt/jdk/default
        ANT_HOME=/opt/tools/apache-ant
        MAVEN_HOME=/opt/tools/apache-maven

        ANT_OPTS="-Xmx4096m"

        PATH=$JAVA_HOME/bin:$ANT_HOME/bin:$MAVEN_HOME/bin:~/.yarn/bin:$PATH

        export JAVA_HOME ANT_HOME MAVEN_HOME PATH ANT_OPTS

2. Launch a new terminal, type:

        sudo apt install vim
        vim ~/.profile

3. Then you'll enter the command mode of vim, which shows the contents of ~/.profile

4. Press "i" to enter the insert mode. 

5. Use arrow keys (↑ ↓ ← →) to move the cursor. 

6. Press "Ctrl+Shift+V" to paste environment variables to the end of content.

7. Press "Esc", type `:wq` to save and quit.

8. Back to the terminal, activate the file.


        source ~/.profile

>Mention:  
If your  directory path is different, please make the corresponding change in environment variables.