# MavenSeleniumPrototype


/////////////////////////
SELENIUM + JENKINS 
/////////////////////////


=====================
MAVEN CUCUMBER PROTOTYPE
=====================
(https://www.youtube.com/watch?v=7336GgdqS7c)

:::::::::::::::::::::::
1) Create New Maven Project in Eclipse
:::::::::::::::::::::::

	1.1 - Use Wizard to create new Maven Project

	1.2 - Edit POM to add dependencies...
		
		junit
			junit
		info.cukes
			cucumber-java
		info.cukes
			cucumber-picocontainer
		info.cukes
			cucumber-junit
			
:::::::::::::::::::::::	
2) Create first test in .feature file
:::::::::::::::::::::::

	2.1 - Place under ...
		
		scr/test/resource
		
	2.2 - Make sure you have Cucumber Feature File Plugin for Eclipse
	
	2.3 - Edit basic .feature file for PoC
	
	2.4 - Create Step Definitions in .java...
		By Using 
			@Given
			@When
			@Then
		Annotations
		
:::::::::::::::::::::::		
3) Create TestRunner Class
:::::::::::::::::::::::
	
	3.1 - Mark it with a 
	
		@RunWith(Cucumber.class)
	
	annotation

	3.2 - Annotate it also with...
		
		@Cucumber.options(
			features = "scr/test/resource"
			)
:::::::::::::::::::::::			
4) RUN!!!
:::::::::::::::::::::::
	
...................................
	4.1) RUN LOCALLY
		
		3 Ways to Run...
			
			A) Run as JUnit Test...
				* Easy, from Eclipse IDE 
				* This is what I do for Tests run locally
		
			B) Run as Maven Test...
				* It's taken as part of the 
					Maven Test
				task
			
				* Ideally, for a Project Build Managed with Maven, this is the desired option
			
			C) Run .feature Files independently
				* From Eclipse:
					With cucumber Eclipse Plugin installed...
						RMB on feature file
						"Run as... Cucumber Feature"
			
...................................
4.2) RUN ON CI SERVER
...................................
	
	++++++++++++++++++++++++++++++++
	4.2.A) Run as JUnit Test
	++++++++++++++++++++++++++++++++
	SOURCES:
	---------------------------------
		+ Run JUnit tests automatically in Jenkins without maven or ant
			
			(			http://stackoverflow.com/questions/16669507/run-junit-tests-automatically-in-jenkins-without-maven-or-ant)
			
		+ How to run JUnit test cases from the command line
			(http://stackoverflow.com/questions/2235276/how-to-run-junit-test-cases-from-the-command-line)
		
		
	4.2.A
	---------------------------------
		.1 - SetUp Project
			* Create a project in Eclipse 
			* Add all projects that contain tests you want to run to its build path
			* Create a class like this:
				import org.junit.extensions.cpsuite.ClasspathSuite;
				import org.junit.runner.RunWith;
				@RunWith(ClasspathSuite.class)
				public class MySuite {}
			* This will execute all JUnit4 testclasses (those containing methods with the @Test annotation) in the projects classpath.
			
		.2 - Run from Command Line
			
			* JUnit 4.X
			
				java -cp /usr/share/java/junit.jar org.junit.runner.JUnitCore [test class name]
				
			* JUnit 3.X
				
				java -cp .:/usr/share/java/junit.jar junit.textui.TestRunner [test class name]
				
		.3 - Create Jenkins Task
		
			* Execute java command
			* Jenkins Machine should have the .jar dependencies in an available path
						

	++++++++++++++++++++++++++++++++
	4.2.B) Run as Maven Test
	++++++++++++++++++++++++++++++++
		SOURCES:
	---------------------------------
		+ Building a maven2 project
		(https://wiki.jenkins-ci.org/display/JENKINS/Building+a+maven2+project)
	
	---------------------------------
	4.2.B
	---------------------------------
		1 - SetUp POM.xml
			** We already have one; have to clean it up
		
		2 - Install Maven Integration Plugin for Jenkins
			** 		
	
	++++++++++++++++++++++++++++++++
	4.2.C) Run .feature Files independently
	++++++++++++++++++++++++++++++++
		* From Eclipse:
			With cucumber Eclipse Plugin installed...
				RMB on feature file
				"Run as... Cucumber Feature"
				
		** ON JENKINS:
			???
		
//////////////////////////////////////////////////////
	MAVEN TUTORIAL
//////////////////////////////////////////////////////
Using JUnit & Maven Surefire
---------------------------
	http://maven.apache.org/surefire/maven-surefire-plugin/examples/junit.html


Understand these Terms...
---------------------------
	parent POM
	<dependencies> section 
	<plugins> section 
	<extensions> section 
	<reporting> section 
	
Maven Plugins for Test Runs
---------------------------
Failsafe Plugin - Integration tests 
Surefire Plugin - Unit tests


Failsafe Plugin
---------------------------
http://maven.apache.org/surefire/maven-failsafe-plugin/
	
	

MAVEN MOJOs
---------------------------
	(http://stackoverflow.com/questions/8420561/what-is-mojo-in-maven)
	
	from http://maven.apache.org/plugin-developers/index.html:

What is a Mojo? A mojo is a Maven plain Old Java Object. Each mojo is an executable goal in Maven, and a plugin is a distribution of one or more related mojos.

In short, a mojo is a maven goal, to extend functionality not already found in maven.

//////////////////////////////////////////////////////
	MAVEN & JENKINS INTEGRATION
//////////////////////////////////////////////////////
How do I run my selenium tests with Jenkins/Maven?
	http://stackoverflow.com/questions/29555130/how-do-i-run-my-selenium-tests-with-jenkins-maven
	
	
	
//////////////////////////////////////////////////////
	GHERKIN en español
//////////////////////////////////////////////////////
	https://josepablosarco.wordpress.com/2015/03/11/lenguaje-gherkin/


	https://github.com/cucumber/gherkin/blob/master/java/src/main/resources/gherkin/gherkin-languages.json
	
================================
gherkin-languages.json	
================================

	"es": {
    "and": [
      "* ",
      "Y ",
      "E "
    ],
    "background": [
      "Antecedentes"
    ],
    "but": [
      "* ",
      "Pero "
    ],
    "examples": [
      "Ejemplos"
    ],
    "feature": [
      "Característica"
    ],
    "given": [
      "* ",
      "Dado ",
      "Dada ",
      "Dados ",
      "Dadas "
    ],
    "name": "Spanish",
    "native": "español",
    "scenario": [
      "Escenario"
    ],
    "scenarioOutline": [
      "Esquema del escenario"
    ],
    "then": [
      "* ",
      "Entonces "
    ],
    "when": [
      "* ",
      "Cuando "
    ]
  },
  
::::::::::::::::::::::::::::::

	#Antecedentes:
	#Pero:
	#Ejemplos:
	#Característica:
	#Dado:
	#Dada:
	#Dados:
	#Dadas:
	#Escenario:
	#Esquema del escenario:
	#Entonces:
	#Cuando:


 
================================
How to translate cucumber/gherkin
================================

http://stackoverflow.com/questions/34257188/where-are-the-translations-in-cucumber-gherkin

--------------------------
Header in Feature File
--------------------------
	* Any language different from en should be explicitly marked with a # language: ... comment at the beginning of your *.feature file:
	
	Example:
	# language: fr
	**Fonctionnalité: ...**
	...
	for French. 
	
	* If you omit this header, Cucumber will default to English (en).
	
	
