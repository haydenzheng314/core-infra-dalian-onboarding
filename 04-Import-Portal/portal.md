# Import portal into IntelliJ:

1. Install Node.js and NPM (Node Package Manager).

    Launch terminal.

        sudo apt install nodejs
        sudo apt install npm

    Once installed, verify them by checking the installed version

        node -v
        npm -v

    >Liferay portal has its own nodejs, and the installed one is only used for IntelliJ.

2. Install JetBrains Toolbox. Download jetbrains-toolbox.tar.gz [here](https://www.jetbrains.com/toolbox-app/).

3. Install IntelliJ IDEA in the toolbox. 
    
    There are Community Edition and Ultimate for your choice. If Ultimate, you need to create a ticket to request IntelliJ IDEA license in JIRA.


4. Open liferay-portal under **project** in toolbox.

    1). Click File -> Project Structure -> Modules

    2). Choose /src/main/java , mark as **Sources**.


# Preparation for ant all

1. Under /home/repo/liferay-portal, create a file named **app.server.your-name.properties**

    Paste the property below into it.

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

2. Create a file named **build.your-name.properties** under the same path.

    Paste the property below into it.

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
#

>About:
>
>You can change server type by uncommenting another one instead if the current one in app.server.your-name.properties
>
>When you run `ant all`, it fails for serveral times at beginning. Because Ant need to import files and actively triggers failure. It tells in terminal.
>
>If it remains, uncomment the URL in build.your-name.properties
