
POET 
=======================

What is this?
--------------

This set of instructions provide and configure the machine to make
automatic test using Nightwatchjs. The following installation and configuration were tested in a new MacBook Air

Java & JDK
--------------

Java is needed to make the automatic tests with Nightwatchjs, so please download and install the latest version of Java
- https://www.java.com/en/download/

Now, the JDK (Java Development Kit) must be installed to use the commands succesfully, download and install the JDK
- http://www.oracle.com/technetwork/java/javase/downloads/index.html

We strongly recommend you restart the computer in this moment. After the installation is finished please verify the version in terminal with the following command.

$ java -version

Selenium WebDriver
--------------

Nightwatch works with the Selenium standalone server, so the first thing you need to do is download the Selenium server jar file `selenium-server-standalone-2.x.x.jar` from the Selenium releases page:
- https://selenium-release.storage.googleapis.com/index.html

To set up and run the Selenium Server, use the following command

$ java -jar selenium-server-standalone-{VERSION}.jar

BrowserStack WebDriver
--------------

Nightwatch works with BrowserStack too, the main difference between these two WebDrivers is that BrowserStack allows you to test in differents OS and devices, use the commands below to install BrowserStack WebDriver

$ ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"

$ brew install node

$ npm install -g browserstack-webdriver

NightwatchJS
--------------
NightWatch can be downloaded or cloned by Git, we recomend the second option, so use the following commands for the installation

$ mkdir /folder/for/the/project

$ cd /folder/for/the/project

$ git clone https://github.com/nightwatchjs/nightwatch.git

$ cd nightwatch/

$ sudo npm install -g nightwatch

Configuration File
--------------

It is recommended to create the file nightwatch.json to set the configuration, this must be created in the project's root folder. In the following link you can download this file.

- https://temas.s3.amazonaws.com/POET/Nightwatch/nightwatch.json

Tests
--------------

The test below navigates to google.com and searches for "rembrandt van rijn"

- https://temas.s3.amazonaws.com/POET/Nightwatch/test1.js

The test below navegates to a ogame.es, in this case you will see how to select an option from a dropdown list and authenticate in the site.

- https://temas.s3.amazonaws.com/POET/Nightwatch/test2.js

The tests should be created in the folder /folder/for/the/project/nightwatch/tests. We recommend to copy the text in the links and create the file in the folder.

$ cd /folder/for/the/project/nightwatch

$ emacs tests/filename.js

Running Tests
--------------

To run the test is necessary to verify that the Selenium server is running, we suggest to use two tabs on terminal.

Tab # 1:

$ java -jar selenium-server-standalone-{VERSION}.jar

Tab # 2: - Test - 

$ cd /folder/for/the/project/nightwatch

$ nightwatch --test/filename.js

Running Tests - Browser Stack
--------------

To run the test in BrowserStack you need to change the settings of the file created before (nightwatch.json). Particularly the "test_settings" section.

"test_settings" : {

    "default" : {
    
      "launch_url" : "http://hub.browserstack.com",
      
      "selenium_port"  : 80,
      
      "selenium_host"  : "hub.browserstack.com",
      
      "silent": true,
      
      "screenshots" : {
      
        "enabled" : true,
        
        "path" : "/tmp"
        
      },
      
      "desiredCapabilities": {
      
        "browserName": "firefox",
        
        "javascriptEnabled": true,
        
    	"os" : " ",
    	
    	"os_version" : " ",
    	
    	"resolution" : " ",
    	
        "acceptSslCerts": true,
        
        "browserstack.user": " ",
        
        "browserstack.key": " "
        
      }
      
    }
    
  }
 
To view all the capabilities that can be configured in this last section using BrowserStack, please access the following link.

- https://www.browserstack.com/automate/capabilities

Remember that you need and account in Browser Stack and fill the fields of "browserstack.user" & "browserstack.key" with the respective account information.

IMPORTANT: BrowserStack records all the simulation, so in the .js MUST exist the end of the process. See the test2.js used before.