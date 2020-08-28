# til_sandy
Repository while learning new things we can write down it here


### Excel
1. To Add row in Excel --> Select row and then press --> ctrl + shift + "+"   :fire:
2. To add multiple row in Excel --> Select multiple rows in excel --> ctrl +shift + "+" :computer: 


### Maven
1. maven clean test is failing since it will first clean the project and then test but the report is opened in the browser
  so maven is not able to clean the project and hence it was failing.


### TestNg
1. Use report ng report it is very easy just do Reporter.log and add the listeners in the testng.xml file 
```code
<listeners>
	<listener class-name="org.uncommons.reportng.HTMLReporter"/>
	<listener class-name="org.uncommons.reportng.JUnitXMLReporter"/>
	</listeners>
```
2. 
