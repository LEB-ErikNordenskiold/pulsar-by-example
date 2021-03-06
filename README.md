Pulsar by Example
=================

Overview
--------
This repository contains example modules for the Pulsar application server.

Workspace setup
---------------
### Prerequisites which must be installed prior to setting up the workspace
* Git (must be present on shell path)
* Apache Ant (must be present on shell path)
* Oracle JDK 7 (must be present on shell path)

### Optional
* [Jetbrains IntelliJ IDEA](https://www.jetbrains.com/idea), Community Edition or better.
    * The workspace configuration assumes that JDK 7 is configured as a SDK in IntelliJ, and named "1.7".

### Installing the workspace

* Install the workspace using _one_ of these two options:

1. Clone the repository [pulsar-by-example repository](https://github.com/DSE-AB/pulsar-by-example) to your local machine

    `cd <local machine project directory>`
    
    `git clone https://github.com/DSE-AB/pulsar-by-example.git`
    
    `cd pulsar-by-example`
    
    If you forked the project on GitHub you might want to set the push url (optional)
    
    `git remote set-url --push origin https://github.com/*Your-GitHub-User-Name-Here*/pulsar-by-example.git` (optional)
    
2. Download the zipped project from GitHub and expand it, then open a shell and cd into the expanded directory.
 
* Run the setup script. *Note: Since the Pulsar environment is downloaded the first time this step 
may take som time to complete.*

    `ant -f script/setup-workspace.xml`
    

### Building the examples and starting Pulsar with IntelliJ IDEA

* Open the top project directory (pulsar-by-example) with IntelliJ IDEA. *Note: You need to open IDEA, then 
select `Open Project` from the splash menu (or choose `Open...` from the file menu) and navigate to select the directory.*
* First you need to build the examples, the simplest way is to use the Ant build script `master-build/dist-all` which will compile and package (dist) all the example modules.
* Start the ´Pulsar (developer)` Run Configuration in Intellij

### Building the examples and starting Pulsar from the command line

Make sure your command shell has the top level project directory as the current directory. The one where this README.md resides.

* Build the example modules

    `ant -f script/build.xml dist-all`
    
* Start Pulsar

    `cd pulsar`
    `java -jar pulsar.launcher-v.v.v.jar`

### Installing the examples    
    
After a few seconds your default web browser will automatically be opened to show the `AdminConsole` UI. 
    
* When the ´AdminConsole´ opens click the ´Install´ tab and install the ´pulsar.devtools.wiki´ module.
* When the module is installed navigate you browser to the page [`/pulsar/wiki/index.html`](http://localhost:8080/pulsar/wiki/index.html) (The default port for Pulsar is 8080, if that is not available Pulsar will use 8081 instead.) 
* The Wiki contains further information on the different example modules and how to use them.
    
    
Project Structure
-----------------
Below you find a description of the project structure. This description doesn't include all directories but aims to 
provide a general guide. Also there are some documented directories that are not yet part of the workspace.

    <top>
    |- .git                 Git Version Control (never modify files here manually)
    |- .idea                IntelliJ project configuration files. Normally these should not be edited manually.
    |                       All files except workspace.xml are under version control
    |- .idea-conf           IntelliJ module configuration files. Only changed when module dependencies are changed.
    |- .gitignore           Git Ignore instructions
    |- README.md            This documentation
    |- dev-tools
    |- dist*                Destination for top level package artifacts
    |- lib
    |   |- test
    |   |- tools
    |- examples
        |- 1-chatter-base
            |- chatter-api
            |- chatter-server
            |- chatter-shellui
        |- 2-chatter-html
            |- chatter-htmlui
        |- 3-chatter-spaui
            |- chatter-spaui
        |- 4-chatter-store
            |- chatter-store
    |- script
    |   |- setup-workspace.xml
    |   
    |   
    |- pulsar*                                              Local developer instance of the Pulsar Application Server
        |- .pulsar-runtime
        |- lib-devel                                        Libraries needed during development of Pulsar modules.
        |- script
        |- logs
        |- conf                                             Logging configuration etc
        |- pulsar.launcher-v.v.v.jar    
        |- pulsar-modules-v.v.v.pulsar 
        |- pulsar-apps-v.v.v.pulsar 
        |- pulsar-endorsed-v.v.v.pulsar
        |- local-dev-link.pulsarlink
    
    * = excluded from version control
    ^ = IntelliJ Module
