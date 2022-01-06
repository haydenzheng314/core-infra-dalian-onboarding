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

# 2. Install Intellij Toolbox and IDEA

Install JetBrains Toolbox. Download .tar.gz [here](https://www.jetbrains.com/toolbox-app/).

Install IntelliJ IDEA in the toolbox. 
    
>There are Community Edition and Ultimate for your choice. 
>
>If Ultimate, you need to create a ticket to request IntelliJ IDEA license in JIRA.
>
>Once you receive the email from JetBrains Sales, use JB account to activate IDEA Ultimate.

# 3. Import portal into IntelliJ:

Open IDEA in toolbox, click File -> Open , select /home/repo/liferay-portal , click OK.

Mark the project directory as a source root:

1. Click File -> Project Structure -> Modules

2. Choose /src/main/java , make sure it's marked as **Sources**.


# 3. Properties Preparation

## 1. app.server.properties

In /home/repo/liferay-portal, create a file named **app.server.username.properties** 

Your `username` is usually set as `liferay`.

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

##
## Server Directory
##

app.server.parent.dir=${project.dir}/../bundles/${app.server.type}
```

>You can change server type by uncommenting another one instead of the current one.

## 2. build.properties

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

>When you run `ant all`, it fails for serveral times at beginning. Because Ant need to import files and actively triggers failure. It tells in terminal.
>
>If failure remains, uncomment the URL in build.username.properties

## 4. Setup Intellij for developing Liferay Portal

In /home/repo , clone the `liferay-intellij` repo:
```
git clone git@github.com:holatuwol/liferay-intellij.git
```

Before executing it, make sure you have run `ant all` for the project.

Go to the root of liferay-portal repo, and run `../liferay-intellij/intellij` . This will create an IntelliJ project containing all modules, with all of them loaded at startup.

Refers to: https://liferay.atlassian.net/wiki/spaces/PRDDXP/pages/1569556027/IntelliJ+for+Liferay+Development