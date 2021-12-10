# 1. Install Node.js and NPM (Node Package Manager).

Launch terminal.

```
sudo apt install nodejs
sudo apt install npm
```

Once installed, verify them by checking the installed version

```
node -v
npm -v
```
>Liferay portal has its own nodejs, and the installed one is only used for IntelliJ.


# 2. Import portal into IntelliJ:

Install JetBrains Toolbox. Download .tar.gz [here](https://www.jetbrains.com/toolbox-app/).

Install IntelliJ IDEA in the toolbox. 
    
>There are Community Edition and Ultimate for your choice. If Ultimate, you need to create a ticket to request IntelliJ IDEA license in JIRA.


Open liferay-portal under **project** in toolbox.

Mark the project directory as a source root:

1. Click File -> Project Structure -> Modules

2. Choose /src/main/java , mark as **Sources**.


# 3. Preparation for ant all

In /home/repo/liferay-portal, create a file named **app.server.username.properties**

Paste the properties below into it.

```
##
## Server Type
## 

#app.server.type=jboss
#app.server.type=tcserver
app.server.type=tomcat
#app.server.type=weblogic
#app.server.type=websphere
#app.server.type=wildfly

## Server Directory

app.server.parent.dir=${project.dir}/../bundles/${app.server.type}
```

Create a file named **build.username.properties** in the same path.

Paste the properties below into it.

```
#
# Set the registry URL to use when invoking NPM via Gradle. Leave the
# property empty to use the default NPM registry.
#

nodejs.npm.registry=
#nodejs.npm.registry=https://registry.npm.taobao.org

#
# Set the alternative node-sass binaries download URL.
#

nodejs.npm.sass.binary.site=
#nodejs.npm.sass.binary.site=http://npm.taobao.org/mirrors/node-sass
```

**About:**

1. You can change server type by uncommenting another one instead if the current one in app.server.username.properties

2. When you run `ant all`, it fails for serveral times at beginning. Because Ant need to import files and actively triggers failure. It tells in terminal.

    If it remains, uncomment the URL in build.username.properties
