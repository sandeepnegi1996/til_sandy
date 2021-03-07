# til_sandy
Repository while learning new things we can write down it here

#### benefit of getters and setter
1. in the below code when we set the value of field number we are checking that is num is less than 10 or if it is greater than 100
2. than in that case what we can do is we can throw some expection
3. but if we do not have setter any value can be set in this.

```java
public void setNumber(int num) {
    if (num < 10 || num > 100) {
        throw new IllegalArgumentException();
    }
    this.number = num;
}

```

#### Why not to declare the private variables ?
1. fields of a class are the implementation details and external class need not to know about the implmentation details 
2. external class should be able to get and set the data.
3. by exposing the details as public we are telling outside classes that it is an actual peice of data that is being stored.
4. if we make the class as public then external or other classes will depend on it which means if in later point of time 
5. we change something then in that case it will also affects other classes.by implementing as method it will improve the flexibility
6. of changing the values in later point in time.
7. **try to make things immutable **

#### Coding guidelines java
1. whenever creating object of stream, or creating connections make sure to close the resources if there is any failure to close the resources 
2. may lead to memory leak which can bring the application down ond later the box on which it is hosted.

#### Non Compliant Code
```java
try {
			FileInputStream input = new FileInputStream(configPath);
			prop.load(input);

		} catch (Exception e) {
			e.printStackTrace();
		}

```

#### Compliant code
1. It was introduced in java 7.
1. Either use finally block to close the resources or use the try with resources.

```java
	try (FileInputStream input = new FileInputStream(configPath);) {

			prop.load(input);

		} catch (Exception e) {
			e.printStackTrace();
		}

```

#### How to create a FAT JAR using maven and eclipse. ?

1. Just put the below mentioned plugin in maven

``` code

<plugin>
    <artifactId>maven-assembly-plugin</artifactId>
    <configuration>
        <archive>
            <manifest>
                <mainClass>com.inventory.gui.InventoryApp</mainClass>
            </manifest>
        </archive>
        <descriptorRefs>
            <descriptorRef>jar-with-dependencies</descriptorRef>
        </descriptorRefs>
    </configuration>
</plugin>

```
2. Now in the maven build in eclipse : "assembly:single"
3. After this A FAT jar that contains all the required libraries will be created and this JAR is a runnable JAR
if we just double click on this JAR or type java -jar runnable.jar , this will be executed.
4. In my case my JAR required some extra files so I need to keep those configuration files , in the same directory where there is the JAR.
5. But I am not able to create a FAT jar using the cmd.
6. 


#### Howt to insert row or column in the excel ?

1. Type Ctrl+Shift+ "+" and then select the option.



#### How to delete a page from microsoft word that is filled with some text

1.Click or tap anywhere in the page you want to delete, press Ctrl+G.
2.In the Enter page number box, type \page.
3.Press Enter on your keyboard, and then select Close.
4.Verify that a page of content is selected, and then press Delete on your keyboard.



#### Type of put request in postman with randomBs

``` json
{
    "summary": "{{$randomBs}}", 
    "pkey": "testr", 
    "issuetype": "test.issuetype.default",
    "applicant": "Test",
    "priority": "default", 
    "sourceSystem": "test",
    "data": {
        "common.field.employee.firstname": "{{$randomFullName}}", 
        "common.field.employee.lastname": "{{$randomLastName}}",
        "common.field.employee.department": "{{$randomDepartment}}",
        "common.field.employee.costcenter": "{{$randomAbbreviation}}",
        "common.field.employee.location": "{{$randomCity}}",
        "rbga.field.termCheck": "yes", 
        "rbga.field.description": "Detailed Description for the request",
        "rbga.field.comments": "Comments",
        "rbga.field.workflowType": "Parallel",
        "rbga.field.wf2": "Serial",
        "rbga.field.wf3": "Serial",
        "rbga.field.parallelWorkflowSel": "One approver approves the request",
        "rbga.field.parallelWorkflowSel2": "All the Approvers has to approve",
        "rbga.field.parallelWorkflowSel3": "All the Approvers has to approve",
        "rbga.field.tempNew": "New Request",
        "rbga.field.approvalstep": "One Step Approval",
        "rbga.field.additionalFields": [ 
            {
                "fields": "fieldname",
                "details": "value"
            }
        ],
        "rbga.field.approver1": {                
            "approvers": [
                {
                    "addAfterEnabled": true, 
                    "deleteFlag": "Yes",
                    "fixed": false,
                    "removable": true, 
                    "userid": "test",
                    "ccList": "test" 
                }
            ],
            "checkDuplicate": "false",
            "maxApprover": "20", 
            "type": "1" 
        },
        "rbga.field.attach": [ 
            {
                "filename": "TypeDataCreation_Catalytic_Schowcase_short.mp4",
                "file": "Base64EncodedString"
            }
        ]
    }
}

```

#### Run the collection using the newman 

	1. Install newman using node js 
	2. First make sure proxy error is fixed
		npm config set registry "http://registry.npmjs.org"
		npm config set strict-ssl false
		npm config set proxy http://"ntid:password"@proxy_url:8080
		npm config set https-proxy http://"ntid:password"@proxy_url:8080
	3. Export the collection
	4. Export the environment variables
	5. Navigate to directory and type :-  newman run collectionname.json -k --environment environment.json
	If some errrors are coming make sure to add -k 
	


#### Testing API automation using postman
1. Add a request and verify it is working from postman, later there is a tab called as tests where you can add all the test scripts
2. We will be testing for the presence of response header, response header values, cookies present, cookies values, response status and much more

```javascript
pm.test("status code is 200",function() {
    pm.expect(pm.response.code).to.eql(200);
});

pm.test("status code text",function() {
    pm.response.to.have.status("OK");
});

//check that the content-type header is present in the response

pm.test("content-type header is present ",function() {
    pm.response.to.have.header("content-type");
});

//check that the header content-encoding is present in response

pm.test("content-encoding header is present",function() {
    pm.response.to.have.header("content-encoding");
});

//check the header transfer-encoding header is present

pm.test("transfer-encoding header is present",function() {
    pm.response.to.have.header("transfer-encoding");
});

//test whether cokkies is present or not

pm.test("Cokkies JESSIONID is present",function() {
    pm.expect(pm.cookies.has('JSESSIONID')).to.be.true;
});

//test the cokkies values for the Expires to be Session

//check the response header for the particular values
pm.test("Content-Type header is application/json",()=>{
    pm.expect(pm.response.headers.get('Content-Type')).to.eql('application/json;charset=UTF-8');
});

//check the response header content-encoding value to be gzip

pm.test("content-encoding is gzip",function() {
    pm.expect(pm.response.headers.get('content-encoding')).to.eql('gzip');
});


//check the transfer-encoding value is chunked

pm.test("transfer-encoding header value is chunked",function() {
    pm.expect(pm.response.headers.get('transfer-encoding')).to.eql('chunked');
})


```
#### Log Rotation and Purging
1. When you are using multiple servers for the tomcat,weblogic etc there is a considerate amount of logs that is being generated
    it is very important to keep in check for these log files
    
2. For this we need to perform log rotation and log purging.
	1. Log Rotation means saving log file with a current time stamp.
	2. Log purging means : 1. Removing the old log files based on retention period
				2. Compress the uncompressed rotated files.
				
we can follow this github script to do the same .

https://github.com/AKSarav/diskspaceman



#### How to break a Website ?

1. Broken links and validator : Verify that there are no broken links on the website.
     1.using the tool web link validator(if website is not open to the world). or W3c link validator
1. No Limit on Form fields length : almost all interactive websites is having some kind of input and there is no limit in the size of text
	that can be entered in the form field. Entering the long text will ultmately crash the website or form will break.
	use the below mentioned link for the long text : https://whiletrue.neocities.org/lte.html
	Fix : website should truncate the unreasonably large text. or block requests that are above a certain size
	
	1. I have tried the above approach the also breaked few websites with the long text.

2. SQL Injection :- send the sql query with the query to the database and it will return some fields 
		    This vulnerability will be there when the developer is not sanitizing the query fields properly.
2. Cross Site Scripting : when something will be written back to the website in that case there is chance that it can lead to 
	cross site scripting attack.
	1. Page content can be modified.
	2. Session cookies could be revealed enabling a perpetrator to impersonate valid users and abuse their private accounts.
	3. To successfully execute a stored XSS attack, a perpetrator has to locate a vulnerability in a web application and then inject malicious script into its 	     server (e.g., via a comment field).
	



#### Daily tasks in corporate ?
1. Fill timesheet
2. Add Sprint wise Testing summary docupedia daily
3. Add the daily bugs in the Bug report
4. Add the vwms updates in weekly and montly updates
5. Discuss with developer and prepare some testcases
6. Add some automation testcases
7. Reply to all the email
8. Meeting and planning for the upcoming weeks


#### How to Apply for leaves in corporate ?

1. Please reconfirm during Sprint Planning of and plan the capacity.  
2. Let us work together to prepare the test cases of 2020.11 release in advance before your leaves so you can begin testing right after your leaves
3. Raise leave request in HRMS (or leave request system).
4. Send out a calendar to your project team in our case it is workon.core
5. Set up Auto reply for these leave dates in Outlook.

#### Preparing for an interview 

below mentioned is the repository we will be using for the coding prepration.

https://github.com/sandeepnegi1996/coding-interview-university
1. The myth of Genius Programmer
	1. Share as much code as you can share the code so that people know what you are working on.
	2. Get Feedback 
	3. Get code reviews
	4. Try something different and then fail : Document when something fails : find the root cause 
	5. I am gonna fail it doesn't matter i will learn more.
	6. Iterate Quickly : fail quickly : 
	7. Practice is the key
	8. Be a small Fish : 
	

#### How to Open the firefox browser in incognito mode using selenium ?
	
	```code
	FirefoxOptions opts=new FirefoxOptions();
	opts.addArguments("-private");
	driver = new FirefoxDriver(opts);
	```

#### 	2. How to Deploy WAR file locally Windows Tomcat Server ?

	1.download apache tomcat
		a. We can run the server using the bin directory and startup.bat in windows or startup.sh in mac
		b. But to deploy the WAR file we need some roles 
		<role rolename="manager-gui"/>
			<role rolename="manager-script"/>
			<user username="admin" password="password" roles="manager-gui, manager-script"/>
		c. These roles we will be adding in the conf/tomcat-users.conf 
		d. Paste the above role it will create user --> username and password to be password ,
		e. No run the startup.bat
		f. Go to localhost:8080 --> deploy a war 
		g. It will ask for username and password  give it 
	
	Application will be deployed.


#### How to Clone a particualar branch 

```code
git clone --single-branch --branch <branchname> <remote-repo>
```


### UDEMY Docker course 
#### Assignment1 

	1. Lesson 1 Docker install and config

	2.Run sudo su --> first then use all the commands
	3.docker container run --publish 80:80 nginx     --> it will run nginx container and map it to port 80 of host

	4.docker container run --publish  80:80 --detach nginx   --> -d is used for the detach 

	5.docker container ls    --> it will show all the running containers

	6.docker container ls -a

	7.docker container run --publish 80:80 --detach --name webhost nginx   --> if we will not give any name than docker give the name by itself

	8.docker container logs webhost  --> it will show all the logs up till now

	9.Docker container top webhost    --> it will show all the processes that are running in the docker container --> in nginx
								We have master and worker process.

	10.Docker container stop webhost
	11.**Docker container rm -f webhost**   --> since we cannot remove running container here we have two choices either stop the container and then remove it or do it 		forefully we are doing it forefully




####Lesson2 : 

	1. Nginx: version
	2. Creates a container based on the image
	3. 80:80   -- > host:container port mapping
	

Lesson 3:

Docker top name_of_container
It will give the running processes in that particular container
Docker container ps  --> will list all the running container 


Containers are like the services runnning on a machine

	
####  Assignments  :wink:
	
	1. Start multiple container 
	2. Docs.docker.com
	3. Run three container nginx,mysql and httpd (apache server
	4. Use -d command
	5. Use --name command
	6. Nginx :--> 80:80 
	7. Httpd:--> 8080:80
	8. Mysql	3306:3306
	9. Use --env for the password in the mysql
	10. Check all containers are ruuning 
	11. Remove all the containers


####  Solution:  :sunglasses:
	1.  -docker run -d -p 3306:3306  -name database1 -e MYSQL_ROOT_PASSWORD=toor  mysql
	2. -docker run --name webhost --publish 80:80 --detach nginx
	3. -docker container run -d --name webserver -p 8080:80 httpd
	4. -docker container stop database1 webhost webserver
	5. -docker container rm database1 webhost webserver
	6. To test hit the public dns with port 80 and 8080




### UDEMY Linux course :green_heart:

Date: 17/9/2020

##### Section3: 

1. First Project
	a. Create new accounts
	b. Check priviliges that the user is having the priviliges to create account
	c. Reports if account creation failed.


##### Additional things :

1. Creating random passwords for the user

	1. Shebang line --> #!/bin/bash
	2. # --> sharp
	3. !  --> bang
	4. Combined called as shebang
	5. What will happen here is basically it will call the bash and pass the filename as the argument
	6. How permission works in linux 
	7. So when you type --> ls -l
	8. -rw-r--r--   1 sandy sandy Date
	9. Here sandy the user will have the -rw --> means read write permission
	10. Sandy second one will be group it will have read permission
	11. Third one is for everyone else in the system they are having just read permission.
	12. -r  --> read the file   (4)
	13. -w   --> change the file content (2)
	14. -x   --> execute the file   (1)
	15. Chmod 755 filename.sh
	16.  -  echo is the shell build in , 
	
	```code
	#!/bin/bash
	
	#it will print some thing
	
	echo 'Just running file for hte first time '
	
	# Assigning a value to a variable
	WORD='Sandeep'
	
	# Double quotes we are using to print the vaiable
	echo "My name is  $WORD"
	
	#What will happen in single quotes with echo
	
	echo '$WORD'
	
	echo "This is another way ${WORD}"
	
	#lets combine two variables
	
	START='sandeep '
	END='negi'
	
	echo "Lets print it together ${START}${END}"
	
	```
	
### Blog post on selenium hub in the docker linux instance :like:
1.STEPS 

```code
	1. Updating linux Server
		a. sudo apt-get update
		b. sudo apt-get upgrade


	2. Installing open jdk 1.8
		a. sudo apt-get install openjdk-8-jdk

	3. Installing docker 
		a. sudo apt-get install \
		    apt-transport-https \
		    ca-certificates \
		    curl \
		    gnupg-agent \
		    software-properties-common
		
		b. curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
		c. sudo apt-key fingerprint 0EBFCD88
		 sudo add-apt-repository \
		   "deb [arch=amd64] https://download.docker.com/linux/ubuntu \
		   $(lsb_release -cs) \
		   stable"
		
		
		d.  sudo apt-get update
		 sudo apt-get install docker-ce docker-ce-cli containerd.io
		
	4. Installing docker compose
		a. sudo curl -L "https://github.com/docker/compose/releases/download/1.27.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
		b. sudo chmod +x /usr/local/bin/docker-compose
		

	5. Make Sure the Custom TCP is enabled on the port number :4444 .
	6. Creating a yml file for the Selenium hub
		a. vi docker-compose-v3.yml
		b. Paste the below mentioned content in this file
		
		version: "3"
services:
  selenium-hub:
    image: selenium/hub:3.141.59-20200826
    container_name: selenium-hub
    ports:
      - "4444:4444"
		chrome:
    image: selenium/node-chrome:3.141.59-20200826
    volumes:
      - /dev/shm:/dev/shm
    depends_on:
      - selenium-hub
    environment:
      - HUB_HOST=selenium-hub
      - HUB_PORT=4444
		firefox:
    image: selenium/node-firefox:3.141.59-20200826
    volumes:
      - /dev/shm:/dev/shm
    depends_on:
      - selenium-hub
    environment:
      - HUB_HOST=selenium-hub
      - HUB_PORT=4444
		opera:
    image: selenium/node-opera:3.141.59-20200826
    volumes:
      - /dev/shm:/dev/shm
    depends_on:
      - selenium-hub
    environment:
      - HUB_HOST=selenium-hub
      - HUB_PORT=4444
		
		
		
	7. Run Docker compose 
		a.  sudo docker-compose -f docker-compose-v3.yml up -d
		b. sudo docker container ls

	8. Check the containers are up and running 
		a. sudo docker container ls

	9. Check in the browser that the port is open and able to access the grid console
		a. Serverip:4444/grid/console

	10. Test using eclipse with some basic test case 
	11. Test with generic test cases
	12. Shut down the selenium grid
		a. sudo docker-compose -f docker-compose-v3.yml down
		
		
		
		
```

### Create a blog post on selenium grid 


### How to add a Email subscription form ?  :point_left:
1. go to convertful and create a widget
2. form the wordpress and the plugin
3. goto mailchimp
4. create email list 
5. send email
6. verify that the emails are received using some settings.

[Checkout the link for Tutorial](https://www.youtube.com/watch?v=U43FqbyOUf8&t=762s) 

### How to download the certificate to connect to some remote server ?
1. condition:- So here I am trying  to connect to Windows Exchange Server so that I can read my mail box wether the particular 
		email is present or not.
		
2. It provides soap services to request any kind of information but we are using java client library EWS to request required information from the server
3. When ::smile:: we are trying we are getting error "unable to find valid certification path to requested target" ::angry::
4. For this we need to have the certs that is required for that we have one Program called as InstallCert.java ::happy::
	https://github.com/sandeepnegi1996/InstallCert
			
5. We can compile this program and run this program with our server url and the port number 
			```java Example java InstallCert localhost.com:443
			```
6. This will download the certificate ,then press enter so that it will be saved to the trusted keystore.
7. Ceritificate will be added to the 'jssecacerts' using alias 'some name '
8. Now we use this certificate. ::cool::
		
 

### Email protocols
1. SMTP : **Simple mail transfer protocol** ::mail:: just used to send email to the receipient email server.It can only be used to send emails.
2. IMAP Protocol :- **Internet Message Access Protocol**  IMAP is client server protocol in which email is received and held by your email server.
			1. Only when we request to read a specific email message that will be downloaded from the server.
			2. You can create and manipulate folders on the mail server and delete messages.
3. POP3 Protocol :- **Post Office Protocol** its functionality is similar to the IMAP protocol but here we can download the messages to our computer.
			2. 

### How to enable the hyper-v using powershell
* ```Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All ```



### log4j2.xml
* Below mentioned is the log4j2.xml for the loggers i am using and I have changed the path where the logs needs to be stored in the FileAppender 
   now I have given the logs directory as the directory to store the path for all the application logs.

```
<?xml version="1.0" encoding="UTF-8"?>
<Configuration status="INFO">
    <Appenders>
        <Console name="ConsoleAppender" target="SYSTEM_OUT">
            <PatternLayout pattern="%d{HH:mm:ss.SSS} [%t] %-5level %logger{36} - %msg%n" />
        </Console>
        <File name="FileAppender" fileName="logs//application-${date:yyyyMMdd}.log" immediateFlush="false" append="true">
            <PatternLayout pattern="%d{yyy-MM-dd HH:mm:ss.SSS} [%t] %-5level %logger{36} - %msg%n"/>
        </File>
    </Appenders>
    <Loggers>
        <Root level="debug">
            <AppenderRef ref="ConsoleAppender" />
            <AppenderRef ref="FileAppender"/>
        </Root>
    </Loggers>
</Configuration>


```


### testng
1. way to re run the failed tests implement this method and then also implement one more interface AnnotationTransformer
```java

public class RetryAnalyzer implements IRetryAnalyzer {

	int counter = 0;
	int retryLimit = 3;

	public boolean retry(ITestResult arg0) {

		if (counter < retryLimit) {
			counter++;
			return true;
		}
		return false;
	}

}



public class AnnotationTransformer implements IAnnotationTransformer {

	
	public void transform(ITestAnnotation annotation,Class testClass,Constructor testConstructor,Method testMethod) {
		annotation.setRetryAnalyzer(RetryAnalyzer.class);
	}


```

### Error
1. Sometimes I edit an excel that is used in the program and then run the code i get the error this is since  
   I am some kind of dumb who forgets to close the file :boom:

### Keyboard Shortcuts
1. Select a word :- ctrl+shift+LeftArrow

### Bash
1. Always use printf "instead of echo";
2. To give next line  printf "\n";

### Java
1. When we are creating string by concat it will create a new String on each contatenation in that function definitely we wanted
   to return the final string as the output.In this case we will be creating numerous number of Strings to overcome this **StringBuilder**
   comes whose object act as the normal string and you can just append to one object and later on return the final StirngBuilder object 
   isn't it cool :cool:
   
   
1. When ever we are writing in a file we open the output stream at the last we will not keep the stream open
1. How to read from the config.properties : - 
	1.Step1: create object of properties
	2. Create object of fileInputStream and give the file path
	3. load the input stream
	4. use the method prop.getProperty to get the content of the properties files
```java

		String rootdirConfig = System.getProperty("user.dir")+"\\src\\main\\resources\\config.properties";
		Properties prop=new Properties();
		FileInputStream input=new FileInputStream(rootdirConfig);
		prop.load(input);
		String to= prop.getProperty("to_config");
		String from=prop.getProperty("from_config");

```
2. Whenever we read something from the properties files it will be string :smile: but we if we need an int value
   we can use Integer.parseInt(prop.getProperty("age")) :boom: this function will convert the string to int.
   

### Eclipse
1. sometime when we press ctrl+1 to load the imports it doesn't work in that case just close the project from ide and open it again.

### Excel
1. To Add row in Excel --> Select row and then press --> ctrl + shift + "+"   :fire:
2. To add multiple row in Excel --> Select multiple rows in excel --> ctrl +shift + "+" :computer: 


### Maven
1. maven clean test is failing since it will first clean the project and then test but the report is opened in the browser
  so maven is not able to clean the project and hence it was failing.
  
2. How to run a single test using maven
	mvn test -Dtest=TestCase_report


### surefire-plugin
1. to store all the xml files in one folder and  give that folder path.
    This is how we can give the XMLFiles --> folder name and we don't need to change anything in the testng.xml since all the other xml are in the same folder to.
    
```
<plugins>
				<plugin>
					<groupId>org.apache.maven.plugins</groupId>
					<artifactId>maven-surefire-plugin</artifactId>
					<version>3.0.0-M4</version>
					<configuration>
						<suiteXmlFiles>
							<suiteXmlFile>XMLFiles/testng.xml</suiteXmlFile>
						</suiteXmlFiles>
					</configuration>
				</plugin>
				
```


### TestNg
1. Use report ng report it is very easy just do Reporter.log and add the listeners in the testng.xml file 
```code
<listeners>
	<listener class-name="org.uncommons.reportng.HTMLReporter"/>
	<listener class-name="org.uncommons.reportng.JUnitXMLReporter"/>
</listeners>
```
2. 
