# maven-setup-instructions

Maven is a build automation tool primarily used for java projects.In software development,"Build" is a process of creating a final application in the form of executables or binaries by combining and compiling all the required source code.Build process for a  simple peice of code like a "hello world!" would not be complicated but in the case of huge projects there might be several dependencies and plugins required to make an executable.In such cases , a set of instructions to add the plugins and dependencies required must be given during build automation. Maven takes this information from pom.xml file. Therefore to use maven for build automation pom.xml file is required.

## SETTING UP MAVEN ON JENKINS:
1. Install JDK (if you haven't)
2. Install Maven:
   - on ubuntu : `sudo apt-get install maven`
   - on mac: usually comes with java
3. Get Maven & Java home locations: 
   - run `mvn -v | awk 'FNR==2 {print $3}'` to get maven home directory 
   - run `mvn -v | awk 'FNR==4 {print substr($3,1,34)}'` to get java jdk location
4. Login to jenkins and in the Jenkins Dashboard:
    - manage Jenkins > Global Tool Configuation
    - click on "JDK installations"
    - enter name(example:jdk) and JAVA_HOME(from step 3)
    - click on "MAVEN installations"
    - enter name(example:maven) and MAVEN_HOME(from step 3)
    - click on apply and save
5. Get back to jenkins default dashboard
   - click on "New Item"
   - enter a name for the project
   - choose "Freestyle project" as project type
   - click "ok"
6. Configure the project:
   - in Source code management, choose git
   - enter the path any java project with a pom.xml file. For understanding purposes, refer to [Pom.xml Reference](https://maven.apache.org/pom.html)
   - in Build, click on advanced
   - choose the maven version configured in step 4
   - give the path to Pom.xml file
   - enter Goals (for ex: clean install)
   - click apply and save
7. Cick on "build now"
8. After build completes, look at the console output. We can see "build success"
9. We can find the packaged files in the workspace directory of the job, in 'target' folder 

References:
- https://maven.apache.org/guides/getting-started/maven-in-five-minutes.html
- https://maven.apache.org/
- http://www.vogella.com/tutorials/ApacheMaven/article.html
- https://github.com/sonatype/maven-example-en
