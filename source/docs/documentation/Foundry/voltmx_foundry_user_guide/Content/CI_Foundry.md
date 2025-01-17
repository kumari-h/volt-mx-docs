---
layout: "documentation"
category: "voltmx_foundry_user_guide"
---
                              

User Guide: Continuous Integration with Volt MX Foundry MFCLI

Continuous Integration with Volt MX Foundry
==========================================

[Continuous Integration](https://en.wikipedia.org/wiki/Continuous_integration) is a key modern day software development practice. Any software development project doing Agile development probably would be doing Continuous Integration (CI) too.

Volt MX  Foundry being a SDLC tool, supports Continuous Integration.  Volt MX Foundry has REST APIs for import/export of an application and publish/unpublish of an application to facilitate CI.  You can consume these REST APIs directly if needed.  For this, refer to the [Continuous Integration with Volt MX Foundry APIs](CI_with_Foundry_APIs.html)documentation. 

While deploying the application to different environments, you may need to reconfigure certain properties, such as the end-point URL to which the application should talk in the production environment. For these kind of reconfiguration, you can use the [Reconfiguration at Publish](ReconfigPublish.html) support. You can set environment specific properties as one time activity using Volt MX Foundry Console and these will automatically get applied during publish in CI flow.

Volt MX  Foundry Command Line Utility
-----------------------------------

Using REST APIs may not be ideal in some cases.  For example, a developer uses a shell script for Continuous Integration, then calls REST APIs and does all the response handling. The process can become tedious and time-consuming.  To make such scenarios easier, we offer Volt MX Foundry Command Line Utility.  The utility helps you export/import or publish/unpublish an application on on-premise Volt MX Foundry and Volt MX Cloud environments.

### Download Links

Volt MX  Foundry Command Line Utility can be downloaded from [VoltMX download center](https://hclsoftware-fno.flexnetoperations.com/flexnet/operations/startPage).

### Examples

This section will help you better understand the utility. For example, company MoBoCo is developing the app MoBoApp. Some of the app's developers use the development environment called DevEnv1. As part of the continuous integration job that runs every night, the team wants to push the MoBoApp from DevEnv1 to QAEnv1 . The team wants automation and testing to occur at night and the following day. Consider the following scenarios.

Scenario 1 – Promoting an app from the local development environment to local QA environment every night

There is one Volt MX Foundry Console connected to two environments – DevEnv1 and QAEnv1.  The following image shows the Volt MX Foundry topology:

![](Resources/Images/CI_MF_655x372.png)

Using the preceding topology to promote the MoBoApp from DevEnv1 to QAEnv1 every night, a user can do the following:

{% highlight voltMx %} java -jar mfcli.jar Publish -u ciuser@moboco.com -p ciuserpwd -e QAEnv1 -a MoBoApp -au http://10.10.25.18:8080 -cu http://10.10.25.18:8080
{% endhighlight %}

Here, `ciuser@moboco.com` is the user with password `ciuserpwd`. The user's account helps to promote the `MoBoApp` to `QAEnv1`. Identity (Auth) Service and Console are running on `http://10.10.25.18:8080`. You can also encrypt the password before exporting an app.

> **_Note:_** The publish command could be used to publish a new application or to overwrite an existing application.

The following example shows how the publish command is used:

{% highlight voltMx %} To publish an application from an on-premise installation,  
java -jar mfcli.jar Publish -u [user] -p [password] -e [environment name] -a [app name] -au [Identity Service URL] -cu [Console URL]
{% endhighlight %}

If the end-point URL or any other property is different in QA environment, you can use the [Application Reconfiguration](ServiceReconfig.html) support to set these properties at one time action in Volt MX Foundry Console. The environment specific properties will automatically get applied every time you publish.

Scenario 2 – Promoting an app from the local development environment to QA environment running on Volt MX Cloud every night

This case is more complex. Developers are working against a local environment (DevEnv1), but QA is testing through an environment in Volt MX Cloud (QAEnv1). There are **two MF Consoles**. The example is a hybrid scenario of on-premise and the cloud. The following image shows the Volt MX Foundry topology:

![](Resources/Images/CI_Cloud_663x412.png)

In this example, a user needs to perform the following four steps:

1.  Encrypt the password of a user who needs to promote the `MoBoApp`  to  `QAEnv1account`.
2.  Export the app from DevEnv1 (as a .zip file).
3.  Import the app (as a .zip file) into Volt MX Cloud account.
4.  Publish the app to QAEnv1.

### Minor difference between on-premise Volt MX Foundry and Volt MX Cloud

The command line utility supports on-premise Volt MX Foundry and Volt MX Cloud. However, there are minor differences in command-line arguments. For on-premise, the utility needs to know the URL of the Identity Services and Console. For Volt MX Cloud, since the URL is constant ([](https://manage.hclvoltmx.com/)[https://manage.hclvoltmx.com](https://manage.hclvoltmx.com/)), and is hard-coded into the utility for convenience. However, Volt MX Cloud is a multiple account (tenant) service, and a user must specify the account ID using –t option. The Volt MX Cloud account ID is a nine-digit number (such as 100054321) and is located in the top-right corner of the console.

In the scenario, a user must perform the following steps:

1.  **Encrypt the password**.
    
    To encrypt the password, run the following command.
    
    {% highlight voltMx %} java -jar mfcli.jar  encrypt password ciuserpwd
    {% endhighlight %}
    
    An encrypted password is generated for the preceding ciuserpwd. Use the encrypted password in the following commands in the scenario.
    
2.  **Export the app from DevEnv1 (as a zip file)**

To export the app, a user must run the following command.

{% highlight voltMx %} java -jar mfcli.jar Export -u ciuser@moboco.com -p encrypted_password -a MoBoApp –f .\MoBoApp.zip -au http://10.10.25.18:8080 -cu http://10.10.25.18:8080.
{% endhighlight %}

In the scenario, ciuser@moboco.com is the user with password  encrypted\_password. The user's account helps to export the `MoBoApp` as `MoBoApp.zip`. The Identity (Auth) Services and console are running on http://10.10.25.18:8080.

The following is an example of how the export command is used:

{% highlight voltMx %} 

To export an application from an on premise installation,

java -jar mfcli.jar Export -u [user] -p [encrypted_password] -a [app name] -f [file name] -au [Identity URL] -cu [Console URL]


{% endhighlight %}8.  **Import the app (as a zip file) into Volt MX Cloud Account**{% highlight voltMx %} java -jar mfcli.jar Import -u ciuser@moboco.com -p encrypted\_password -a MoBoApp –f .\\MoBoApp.zip –t 100054321
    {% endhighlight %}

In the example, ciuser@moboco.com is the user with encrypted\_password. The user's account helps to import the MoBoApp from MoBoApp.zip.

> **_Note:_** Since no URL is provided for Identity Service and console, it is assumed that the URL is Volt MX Cloud ([](https://manage.hclvoltmx.com/)[https://manage.hclvoltmx.com](https://manage.hclvoltmx.com/)). Since Volt MX Cloud is a multiple tenants (account) service, a user must specify the account ID using –t. The account ID in the preceding example is 100054321.

> **_Note:_** In the example, it is assumed a user is trying to overwrite the existing MoBoApp in the account. If this is new application, then do not specify any name with -a option.

The following is an example of how the import command is used:

{% highlight voltMx %} 

To import an application to manage.hclvoltmx.com,

java -jar mfcli.jar import -u <user> -p <password> -t <account id> [-f <file name> | -r <directory name>] [-a <app name>] [-v <app version>] [-ay] [-to <time in secs>]


{% endhighlight %}14.  **Publish the app to QAEnv1**{% highlight voltMx %} java -jar mfcli.jar Publish -u ciuser@moboco.com -p encrypted\_password -e QAEnv1 -a MoBoApp –t 100054321
    {% endhighlight %}

This method is similar to local publish, except the -t option specifies the account ID.

The following is an example of how the publish command is used:

{% highlight voltMx %} To publish an application to manage.hclvoltmx.com,  
  
java -jar mfcli.jar Publish -u [user] -p [encrypted_password] -e [environment name] -a [app name] -t [account id]
{% endhighlight %}

If the end-point URL or any other property is different in QA environment running on Volt MX Cloud, you can use the [Application Reconfiguration](ServiceReconfig.html) support to set these properties at one time action in Volt MX Foundry Console. The environment specific properties will automatically get applied every time you publish.

### Miscellaneous Features

#### Get Usage

Get the usage:

{% highlight voltMx %} For example, to get summary help on all the commands,  
java -jar mfcli.jar help  
  
Following commands are supported:-  
  
    `account-config`     Gets Auth url information for the Volt MX Foundry Command Line Utility can be downloaded from [VoltMX download center](http://community.hclvoltmx.com/downloads). Foundry installation. Applicable for on-premise installation only.  
    `appinfo`             Displays the App key, App Secret and Service URL for an application  
 `authenticate`         Authenticates user with given credentials and returns the Identity token  
`binary-upload`      Uploads a client binary to Foundry. [Click here for more details on the binary-upload command](CI_NativeUploadPublish.html)  
  
`build`               Command to build Iris apps for different channels. [Click here for more details on the build command](CI_CloudBuild.html)  
`build-cancel`       Command to cancel build for iris project
    `build-download`     Command to download artifacts for given build
    `build-status`       Command to check build status or fetch status url for given build
    `build-trigger`      Command to trigger build for iris project
    `build-upload`       Command to upload iris project for build  
  
    `diagnostics`        Gets the diagnostics information from the Volt MX Foundry installation. Applicable for on-premise installation only.  
  
    `encrypt`            Generates an encrypted password from plain text password using default key. To use custom encryption key, set the property password.encryption.key.  
    `explore-snapshots` Displays the details of the available snapshots.[Click here for more details on Promote a Deployment Package command](AppPromotion.html)  
`export`             Exports the specified application as a .zip file or a directory  
    `export-config-properties` Exports the configurable properties as a specified .zip file or directory. [Click here for more details on the `export-config-properties` command](Export_Import_Configuration_Parameters_AppServices_MFCLI.html#import-operation-for-configurable-parameters-app-services).`  
  
export-dashboards` Export the custom dashboards from Foundry.  
   `export-deploymentpackage` Exports the deployment package of a snapshot. [Click here for more details on Promote a Deployment Package command](AppPromotion.html)  
`export-reports`     Export custom reports for a specified application from Foundry.
    `export-service`     Exports the specified service as a .zip file or a directory  
    `export-config`   Exports the existing integration, identity and object Service Configuration profile, for the given app and environment. Profile is downloaded as the specified .json file. [Click here for more details on the export-config command](ServiceConfigProfile.html#export-import-service-profiles-using-mfcli)  
`generate-docs`      Generates HTML documentation for the specified Volt MX Foundry application along with the OpenAPI (Swagger) file
    `healthcheck`        Gets the health check information for the environment.
    `help`               Help on the tool or specific command
    `import`             Imports the specified .zip file or the directory as an application  
`import-config-properties` Imports the specified .zip file or the directory as configurable properties file. ``[Click here for more details on the `import-config-properties` command](Export_Import_Configuration_Parameters_AppServices_MFCLI.html#import-operation-for-configurable-parameters-app-services).```  
import-dashboards`  Import the custom dashboards into Foundry.
    `import-reports`     Import the custom reports for a specified application into Foundry.
    `import-service`     Imports the specified .zip file or the directory as a service  
    `import-config`   Imports the specified Service Configuration profile .json file,into the given app and environment. [Click here for more details on the import-config command](ServiceConfigProfile.html#import-config-command).  
`license`            Gets the license information from the Volt MX Foundry installation. Applicable for on-premise installation only.
    `lock-config`        Command to lock services given a lock configuration json and an App zip. Creates a clone of the provided app with lock configuration applied. [Click here for more details on lock-config command](Lock_Unlock_Fields_ObjectServices_MFCLI.html)[  
](Lock_Unlock_Fields_ObjectServices_MFCLI.html)    `merge-service-zip`  Merges a given service package with a template package.  
    `merge-app-zip`  Merges a given app package with a template package. [Click here for more details on merge-app-zip command](Merge_Templates_using_MFCLI.html#mergeapppackage)   
`native-publish`     Publishes the native binaries to the environment. [Click here for more details on native-publish command](CI_NativeUploadPublish.html)      
    `promote-deploymentpackage` Promotes the imported deployment package to the environment. [Click here for more details on Promote a Deployment Package command](AppPromotion.html).  
    `publish`             Publishes the application to the environment.
    `publish-cancel`     Cancel an in-progress publish/unpublish of an application to an environment.
    `publish-status`     Queries the publish/unpublish status of an application in an environment.
    `set-appversion`     Sets a particular version as default among all successfully published versions of an app.
    `unlock-config`      Command to remove all lock configurations from the provided App zip. Creates a clone of the provided app with locks removed. [Click here for more details on unlock-config command](Lock_Unlock_Fields_ObjectServices_MFCLI.html)  
`unpublish`          Unpublishes the application from the environment.
    `wrap`               Wraps an existing client binary with Volt MX Foundry SDK for getting analytics. Applicable for Volt MX Cloud only.
    `wrap-delete`        wrap-delete command delete the analytics app and the stats captured will be not be accessible. Applicable for Volt MX Cloud only.
    `wrap-fetch`         Fetch wrapped client binary. Applicable for Volt MX Cloud only.  
  
  
Usage: Run the self-executable JAR with relevant arguments.   
 -u [user]           : Volt MX user required for authentication, for example, abc@voltmx.com  
  
 -p [password]       : Password of the Volt MX user. This could be plain text or encrypted using
       'encrypt' command.  
 -t [account id]     : 9 digit id of the Volt MX Cloud account (visible in top right corner in Console), for example, 100054321. Not relevant for an on-premise installation.  
  
 -a [app name]       : Name of the app to be published/unpublished/exported/imported. If importing a new app, this should not be specified.  
  
 -e [environment name]: Name of the environment to publish to/unpublish from. Not relevant for import/export.  
   
\-f [file name]       : Name of the exported file or file to import. For example, c:\\tmp\\app.zip. Not relevant for publish/unpublish.  
   
\--release-lock      : Forcibly release lock taken by previous operation (use with caution) when doing publish/unpublish. Default: false  
  
\-au [Identity URL] : URL of Volt MX Foundry Identity Services, relevant for on premise installation only. For example, http://10.10.24.79:8080  
  
\- cu [Console URL]   : URL of Volt MX Foundry Console, relevant for on premise installation only. For example, http://10.10.24.78:8081  
  
\-r, --directory    : Name of the directory to export to or import from. For example, C:\\src\\MyApp. Either -f or -r has to be specified.

--skipwebapp	    :	If true, skips the publish of web app/zip during app publish. Default: false
  
\--mfa
       If specified, multi-factor authentication is enabled. The secret key for
       multi-factor authentication required for generating one time password (OTP) needs to
       be specified in the properties file.
       Default: false  
       For more details to enable MFA, refer [Support for Multi-Factor Authentication from MFCLI](MFA_for_CLI.html)  
  
  -v, --version
       Version of the app to be imported, defaults to the version info present
       in the package. If version info is not present in package, defaults to 1.0.
       Default: 1.0  
  
  
To get more information on a specific command, type 'java -jar mfcli.jar help <command>'  
For example, to get detailed help on a particular command including examples on publish,   
java -jar mfcli.jar help publish  
  
  
To get details of an application from for Volt MX Cloud (manage.hclvoltmx.com) environment  
java -jar mfcli.jar appinfo -u <user> -p <password> -t <account id> -a <app name> [-v <app version>] -e <environment name>  
java -jar mfcli.jar appinfo -u abc@voltmx.com -p password -t 100054321 -a MyApp -v 2.0 -e MyEnv  
  
  
To get details of an application from on-premise installation  
java -jar mfcli.jar appinfo -u <user> -p <password> -au <Identity URL> -cu <Console URL> -a <app name> [-v <app version>] -e <environment name>  
java -jar mfcli.jar appinfo -u abc@voltmx.com -p password -au http://10.10.24.79:8080 -cu http://10.10.24.78:8081 -a MyApp -v 2.0 -e MyEnv  
  
  
To publish an application to manage.hclvoltmx.com,  
java -jar mfcli.jar Publish -u [user] -p [password] -e [environment name] -a [app name] -t [account id] [--skipwebapp]  
java -jar mfcli.jar Publish -u abc@voltmx.com -p password -e MyEnv -a MyApp -t 100054321 --skipwebapp  
  
To publish an application to an on-premise installation,  
java -jar mfcli.jar Publish -u [user] -p [password] -e [environment name] -a [app name] -au [Identity URL] -cu [Console URL] [--skipwebapp]  
java -jar mfcli.jar Publish -u abc@voltmx.com -p password -e MyEnv -a MyApp -au http://10.10.24.79:8080 -cu http://10.10.24.78:8081 --skipwebapp  
  
To unpublish an application from manage.hclvoltmx.com,  
java -jar mfcli.jar Unpublish -u [user] -p [password] -e [environment name] -a [app name] -t [account id]  
java -jar mfcli.jar Unpublish -u abc@voltmx.com -p password -e MyEnv -a MyApp -t 100054321  
  
To unpublish an application from an on-premise installation,  
java -jar mfcli.jar Unpublish -u [user] -p [password] -e [environment name] -a [app name] -au [Identity URL] -cu [Console URL]  
java -jar mfcli.jar Unpublish -u abc@voltmx.com -p password -e MyEnv -a MyApp -au http://10.10.24.79:8080 -cu http://10.10.24.78:8081  
  
To export an application from manage.hclvoltmx.com,  
java -jar mfcli.jar Export -u [user] -p [password] -a [app name] -t [account id] -f [file name] | -r <directory name>  
java -jar mfcli.jar Export -u abc@voltmx.com -p password -a MyApp -t 100054321 -f "c:\\tmp\\ExportedApp.zip"  
  
To export an application from an on-premise installation,  
java -jar mfcli.jar Export -u [user] -p [password] -a [app name] -f [file name] -au [Identity URL] -cu [Console URL]  
java -jar mfcli.jar Export -u abc@voltmx.com -p password -a MyApp -f "c:\\tmp\\ExportedApp.zip" -au http://10.10.24.79:8080 -cu http://10.10.24.78:8081  
  
To import an application to manage.hclvoltmx.com,  
java -jar mfcli.jar import -u <user> -p <password> -t <account id> [-f <file name> | -r <directory name>] [-a <app name>] [-v <app version>] [-ay] [-to <time in secs>]  
  
java -jar mfcli.jar Import -u abc@voltmx.com -p password -a MyApp -t 100054321 -f "c:\\tmp\\AppToImport.zip"  
  
  
**\-v, --version** If present overwrites only an existing version of the apps. It there is no existing app version, the import command is terminated.  
  
**\-ay, --async** If present imports the app asynchronously, polls and responds the status.   
Default: false  
  
**\-to, --timeout** If present Timeout in seconds for asynchronous import. Polls the status of import until the given timeout.  
Default: 300  
  
To import an application to an on-premise installation,  
java -jar mfcli.jar import -u <user> -p <password> -au <Identity URL> -cu <Console URL> [-f <file name> | -r <directory name>] [-a <app name>] [-v <app version>] [-ay] [-to <time in secs>]  
  
java -jar mfcli.jar Import -u abc@voltmx.com -p password -a MyApp -f "c:\\tmp\\AppToImport.zip" -au http://10.10.24.79:8080 -cu http://10.10.24.78:8081  
  
To encrypt a password,  
For example, to encrypt password 'mypassword',
  java -jar mfcli.jar encrypt mypasswordOr,
  java -DVOLTMX_MFCLI_ENCRYPTION_KEY=2d04b412-64cc-4066-a6c8-9c1417b9b85f -jar mfcli.jar encrypt mypassword  

{% endhighlight %}

#### Unpublish Command

The Unpublish feature helps you undo the publish command. The syntax for the Unpublish command is that same as the publish command's. For republish, do not unpublish.  To overwrite an existing publish, republish by executing the publish command again.  When a user does unpublish, all of the app's metadata are removed. The next publish creates fresh metadata, such as a new app key/secret. In case of republishing, when a user does publish multiple times to republish an app, all of the app's metadata are retained.

#### Authenticate API

If you have log in credentials, this authenticate command helps you to get the Auth Token out of your login credentials. For example, you can use this command to get a valid Volt MX Identity token and be able to use that token with subsequent REST API calls to interact directly like using Engagement service APIs or AppFactory APIs.

The API supports for Volt MX Auth and External auth services.

{% highlight voltMx %}for Volt MX Cloud (manage.hclvoltmx.com) environment,
java -jar mfcli.jar authenticate -u <user> -p <password> -t <account id>
java -jar mfcli.jar authenticate -u abc@voltmx.com -p password -t 100054321
{% endhighlight %}{% highlight voltMx %}for on-premise installation,
java -jar mfcli.jar authenticate -u <user> -p <password> -au <Identity URL> -cu <Console URL>
java -jar mfcli.jar authenticate -u abc@voltmx.com -p password -au http://10.10.24.79:8080 -cu http://10.10.24.78:8081
{% endhighlight %}{% highlight voltMx %}To use external authentication
java -jar mfcli.jar authenticate -u <user> -p <pasword> -t <accountid> --external-auth
{% endhighlight %}

#### Force Release Lock

This utility guarantees a consistent operation during the preceding import/export/publish/unpublish commands.  The utility ensures that only one such operation per app occurs at a given time.  To do this, the utility takes a lock in the database. If there is a software defect, the DB lock is not freed. A user can use `--release-lock` to force the lock release. This option should be used with caution because it can cancel any existing app publish.
