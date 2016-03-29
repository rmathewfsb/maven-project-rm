Advanced Anypoint Platform Development - Snippets

*******************************************************************

*** MODULE 1: Managing Mule Projects with Maven *******************

*** WT 1-1: settings.xml  *****************************************

URL: http://mu.mulesoft-training.com/maven/settings
username: muletraining.nexus
password: MuleTraining

*** MODULE 2: Managing Mule Code **********************************

*** WT 2-1: README.md **********************************************

# maven-project

This is my Maven project from MuleSoft's advanced development class

## How to run the project

1. Add the remote repository: `git remote add origin https://github.com/rmathewfsb/maven-project-rm.git`

1. Enter the repo: `cd maven-project`

1. (Optional) Set your MULE_HOME env variable: `export MULE_HOME={locationOfMuleInstall}`

1. Package and deploy: `mvn install` 


*** MODULE 3: Continuous Integration ********************************

*** WT 3-1: Jenkins Server ******************************************

URL: http://adv.mulesoft-training.com
username: mulesoftdev
password: L3arnmule

*** WT 3-2 Test *****************************************************

 @Test
 public void retrieveFlightsAddsAppropriateHeader() throws Exception {
   MuleEvent event = runFlow("retrieveFlights");
   String contentType = event.getMessage().getOutboundProperty("Content-Type");
   assertEquals("application/json", contentType);
 }
 
*** WT 3-3: Mule Maven plugin  ************************************* 

<plugin>
    <groupId>org.mule.tools.maven</groupId>
    <artifactId>mule-maven-plugin</artifactId>
    <version>2.0</version>
    <configuration>
        <deploymentType>cloudhub</deploymentType>
        <muleVersion>3.7.2</muleVersion> 
        <username>yourUsername</username>
        <password>yourPassword</password>
	 <workerType>Micro</workerType>
        <redeploy>true</redeploy>
        <environment>Production</environment>
    </configuration>
    <executions>
        <execution>
            <id>deploy</id>
            <phase>deploy</phase>
            <goals>
                <goal>deploy</goal>
            </goals>
        </execution>
    </executions>
</plugin>

*** Module 4: Driving Development with MUnit **************************

*** WT 4-1: Mock payload data *****************************************  
    
#[[{'orderID':444, 'location':'international','price':14.01}, {'orderID':444, 'location':'international','price':14.01}, {'orderID':555, 'location':'domestic','price':14.01}]]

*** WT 4-1: Map payload data ****************************************** 

#[{'international': java.util.Map<String,String>[], 'domestic': java.util.Map<String,String>[]}]

*** WT 4-1: Mock payload data 2 ***************************************** 

#[[{'orderID':444, 'location':'international','price':14.01}, {'orderID':444, 'location':'international','price':14.01}]]

*** Module 9: Securing Communication with SSL **************************

*** WT 9-1: Generate server key store ********************************** 

keytool -genkey -keyalg RSA -alias selfsigned -keystore serverStore.jks -storepass password -validity 360 -keysize 2048

*** WT 9-2: Generate client key store ********************************** 

keytool -genkey -keyalg RSA -alias selfsigned -keystore clientStore.jks -storepass password -validity 360 -keysize 2048