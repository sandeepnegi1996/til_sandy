# til_sandy
Repository while learning new things we can write down it here



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
