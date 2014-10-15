# Welcome to Test Item Bank #
The Test Item Bank component manages the importing and exporting of test (assessment) items. Major features include:

* OAuth-based security
* RESTful API
* Multi-tenant support

## License ##
This project is licensed under the [AIR Open Source License v1.0](http://www.smarterapp.org/documents/American_Institutes_for_Research_Open_Source_Software_License.pdf).

## Getting Involved ##
We would be happy to receive feedback on its capabilities, problems, or future enhancements:

* For general questions or discussions, please use the [Forum](http://forum.opentestsystem.org/viewforum.php?f=12).
* Use the **Issues** link to file bugs or enhancement requests.
* Feel free to **Fork** this project and develop your changes!

## Usage
The Test Item Bank modules require configuration to be setup in Program Management in order for the modules to configure themselves correctly.  A sample configuration file that includes all the properties can be found in external_release_docs/required-progman-configuration.properties.  The contents of the file can be copied and pasted into Program Management and then modified based on the descriptions below.

* `tib.file.pathname=/usr/local/tomcat/uploads` - Location on the TIB server where TIB will place test items it FTPs from the FTP server.
* `tib.mna.description=The Test Item Bank Component` - Name of TIB component for display in MNA
* `mna.mnaUrl=http://name.of.mna.server/rest/` - URL of the MNA server's REST endpoint
* `tib.mongo.hostname=dns.name.of.mongodb.host` - DNS name of the Mongo DB host for TIB.
* `tib.mongo.port=27017` - TIB Mongo DB server port
* `tib.mongo.username=` - TIB Mongo DB username
* `tib.mongo.password=` - TIB Mongo DB password
* `tib.mongo.dbname=test` - TIB Mongo DB database name
* `tib.sftp.hostname=name.of.sftp.server` - Name of SFTP server from which TIB reads items.
* `tib.sftp.port=22` - TIB SFTP port
* `tib.sftp.user=` - TIB SFTP username
* `tib.sftp.password=` - TIB SFTP password
* `oauth.access.url=https://name.of.sso.server/auth/oauth2/access_token?realm=/sbac` - SSO OAuth service URL including realm 
* `tib.oauth.checktoken.endpoint=https://name.of.sso.server/auth/oauth2/tokeninfo?realm=/sbac` - SSO OAuth checktoken service URL including realm 
* `tib.oauth.resource.client.id=` - OAuth TIB client ID 
* `tib.oauth.resource.client.secret=` -  OAuth TIB client secret
* `mna.oauth.client.id=mna` - OAuth MNA client name
* `mna.oauth.client.secret=` -  OAuth MNA client secret
* `permission.uri=https://name.of.permissions.server/rest` - REST endpoint of Permissions server
* `tib.clean.files.cron.trigger=0 0 8 * * *` - Cron config for cleaning TIB files
* `tib.sftp.import.directory=` - Import directory name in SFTP directory for TIB user
* `tib.clean.files.age.days=100` - How many days to keep files in TIB's SFTP directory on the sftp server
* `component.name=Test Item Bank` - Component name. Must match name in Permissions and Program Management.

### REST Module
The REST module is a deployable WAR file (`test-item-bank.rest-VERSION.war`) that provides REST endpoints that can be used to access and modify test item data.  The REST module has an internal dependency to the Persistence module.

The REST module uses both the Program Management and the Monitoring and Alerting components.  Please view the documentation at the links provided.
The REST module is a deployable WAR file (`test-item-bank.rest-VERSION.war`) that provides REST endpoints that can be used to access and modify test item data.  The REST module has an internal dependency to the Persistence module.

### Persistence Module
The Persistence module is a JAR artifact that is used by the REST module.  This module is responsible for persistence of application data.

### Domain Module
The domain module contains all of the domain beans used to model the Test Item Bank data as well as code used as search beans to create Mongo queries.  It is a JAR artifact that is used by other modules.

## Build
These are the steps that should be taken in order to build all of the Program Management related artifacts.

### Pre-Dependencies
* Mongo 2.0 or higher
* Tomcat 6 or higher
* Maven (mvn) version 3.X or higher installed
* Java 7
* Access to sb11-shared-build repository
* Access to sb11-shared-code repository
* Access to sb11-rest-api-generator repository
* Access to sb11-program-management repository
* Access to sb11-monitoring-alerting-client repository

### Build order

* sb11-shared-build
* sb11-shared-code
* sb11-rest-api-generator
* sb11-program-management
* sb11-monitoring-alerting-client
* sb11-test-item-bank

## Dependencies
Test Item Bank has a number of direct dependencies that are necessary for it to function.  These dependencies are already built into the POM files.

### Compile Time Dependencies
* Apache Commons IO
* Apache Commons Lang
* Hibernate Validator
* Spring Integration Core
* Spring Integration SFTP
* Apache Commons Compress
* Apache Commons File Upload
* CGLib
* SB11 Shared Code
	* Logback
	* SLF4J
	* JCL over SLF4J
	* Spring Core
	* Spring Beans
	* Spring Data MongoDb
	* Mongo Data Driver
	* Spring Context
	* Spring WebMVC
	* Spring Web
	* Spring Aspects
	* AspectJ RT
	* AspectJ Weaver
	* Javax Inject
	* Apache HttpClient
	* JSTL API
	* Apache Commons Lang
	* Joda Time
	* Jackson Core
	* Jackson Annotations
	* Jackson Databind
* SB11 REST API Generator
	* JSTL
	* Apache Commons Lang
* SB11 Program Management Client (view README for dependency details)
* SB11 Monitoring and Alerting Client (view README for dependency details)

### Test Dependencies
* Spring Test
* Hamcrest
* JUnit 4
* Flapdoodle
* Podam
* Log4J over SLF4J
* Mockito

### Runtime Dependencies
* Servlet API
### Runtime Dependencies
* Servlet API