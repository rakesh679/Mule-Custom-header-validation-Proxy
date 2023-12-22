# Mule-Custom-header-validation-Proxy
Mule Custom header validation Proxy



For Custom policy add below configuration in setting.xml
1.
```xml


 <profile>
     <id>archetype-repository</id>
     <repositories>
       <repository>
         <id>archetype</id>
         <name>Mule Repository</name>
         <url>https://repository.mulesoft.org/nexus/content/repositories/public</url>
         <releases>
           <enabled>true</enabled>
           <checksumPolicy>fail</checksumPolicy>
         </releases>
         <snapshots>
           <enabled>true</enabled>
           <checksumPolicy>warn</checksumPolicy>
         </snapshots>
       </repository>
     </repositories>
   </profile>
   
   
<server>
		<id>Exchange2</id>
		<!-- NOTE: In order to be able to publish assets to exchange, this user will need Exchange Contributor Role -->
		<username>anypointusername</username>
		<password>anypointpassword</password>
	</server>   

2.
mvn -Parchetype-repository archetype:generate -DarchetypeGroupId=org.mule.tools -DarchetypeArtifactId=api-gateway-custom-policy-archetype -DarchetypeVersion=1.2.0 -DgroupId=<replace with orggroupid> -DartifactId=custom-Policy -Dversion=1.0.0 -Dpackage=mule-policy

3. If you are using any external jar or shared library like mysql jar or any other jar in policy  while applying we will get error " A-policy-template-artifact-cannot-export-packages"
to resolve this issue all dependency and shared library used in application only where we want to use policy.

4. <distributionManagement>
		<repository>
			<id>Exchange2</id>   
			<name>Corporate Repository</name>
			<url>${exchange.url}</url>
			<layout>default</layout>
		</repository>
	</distributionManagement>

5. If while building getting dependency error related to "HTTP Policy Transform Extension" then add/check mule ee nexus repositories username and password. if dont have nexus username and password remove dependency from pom. but after removal cant perform some task for ref check below url.

https://docs.mulesoft.com/mule-gateway/policies-custom-http-transform
