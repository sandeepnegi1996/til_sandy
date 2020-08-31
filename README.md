# til_sandy
Repository while learning new things we can write down it here


### Error
1. Sometimes I edit an excel that is used in the program and then run the code i get the error this is since  
   I am some kind of dumb who forgets to close the file :boom:

### Keyboard Shortcuts
1. Select a word :- ctrl+shift+LeftArrow

### Bash
1. Always use printf "instead of echo";
2. To give next line  printf "\n";

### Java
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
