# til_sandy
Repository while learning new things we can write down it here


### Blog post on selenium hub in the docker linux instance

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
