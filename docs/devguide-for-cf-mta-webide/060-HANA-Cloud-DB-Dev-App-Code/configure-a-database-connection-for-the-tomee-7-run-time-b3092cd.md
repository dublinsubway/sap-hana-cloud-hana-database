<!-- loiob3092cdd8e754a08a9e86006a53c4cca -->

# Configure a Database Connection for the TomEE 7 Run Time

Configure a data source for TomEE 7.



<a name="loiob3092cdd8e754a08a9e86006a53c4cca__context_azc_zn2_dhb"/>

## Context

The following steps demonstrate how data sources can be configured in such a way that a developer or operator can change the SAP HANA Cloud service used for creating the data source without having to rebuild or release a new version of the application archive.

> ### Note:  
> Since the outdated TomEE 1.7 version is no longer included in the SAP Java Buildpack, it is recommended to migrate to TomEE 7 as soon as possible, as described in the *Apache TomEE Migration Guide* listed in *Related Information* below. TomEE 7 is already included in previous versions of the SAP Java Buildpack.



<a name="loiob3092cdd8e754a08a9e86006a53c4cca__steps_rdj_xgz_jv"/>

## Procedure

1.  Create a `resources.xml` file.

    -   If the data source is to be used from a Web application, you have to create the file inside the `WEB-INF/` directory.
    -   If the data source is to be used from Enterprise JavaBeans \(EJBs\), you have to create the file inside the `META-INF/` directory.

    The `resources.xml` file has to be inside the application's WAR file and has to contain information about the data source to be used.

    > ### Example:  
    > Sample `resources.xml`
    > 
    > ```
    > 
    > <?xml version='1.0' encoding='utf-8'?>
    > 
    > <resources>
    >  <Resource id="jdbc/DefaultDB" provider="xs.openejb:XS Default JDBC Database" type="javax.sql.DataSource" >
    >     service=${service_name_for_DefaultDB}
    >   </Resource>
    > </resources>
    > 
    > ```

    In this example a placeholder is used for the service instance name.

2.  Add the default keys and their values.

    You need to include the data source information in `META-INF/sap_java_buildpack/config/resource_configuration.yml` of the WAR file to define a default value for the placeholder from the previous step.

    -   > ### Example:  
        > Defining a default service in `resource_configuration.yml` for a Web application
        > 
        > ```
        > 
        > ---
        >  tomee7/webapps/ROOT/WEB-INF/resources.xml:
        >   service_name_for_DefaultDB: di-core-hdi
        > ```

    -   > ### Example:  
        > Defining a default service in `resource_configuration.yml` for an EJB
        > 
        > ```
        > 
        > ---
        > tomee7/webapps/ROOT/META-INF/resources.xml:
        >   service_name_for_DefaultDB: di-core-hdi
        > ```


    With this configuration the service used for creation of data sources is determined while staging and *di-core-hdi* is used. To use this method to change the data sources without having to rebuild or make a new release of the application, developers or operators need to perform an additional deployment of the same application archive.

3.  Add the key values to be updated.

    To use a different service instance, you need to provide an environment variable in the `manifest.yml` file, and bind the application to that service instance in the services section of the `manifest.yml` file.

    -   > ### Example:  
        > Defining a new service for the look-up of the data source in a Web application
        > 
        > ```
        > 
        > env:
        >   TARGET_RUNTIME: tomee7
        >   JBP_CONFIG_RESOURCE_CONFIGURATION: "[
        >     'tomee7/webapps/ROOT/WEB-INF/resources.xml':
        >       {'service_name_for_DefaultDB' : 'my-local-special-di-core-hdi'}
        >      ]"
        > 
        > ```

    -   > ### Example:  
        > Defining a new service for the look-up of the data source in an EJB
        > 
        > ```
        > 
        > env:
        >   TARGET_RUNTIME: tomee7
        >   JBP_CONFIG_RESOURCE_CONFIGURATION: "[
        >     'tomee7/webapps/ROOT/META-INF/resources.xml':
        >       {'service_name_for_DefaultDB' : 'my-local-special-di-core-hdi'}
        >      ]"
        > 
        > ```


    With this configuration, when the application starts, the parameters bound for service *my-local-special-di-core-hdi* are read from the environment, a data source is created and bound under `jdbc/DefaultDB`. The application then uses the Java Naming and Directory Interface \(JNDI\) to look up how to connect with the database.


**Related Information**  


[Configure a Database Connection](configure-a-database-connection-d462ffc.md "You can configure your application to use a database connection so that the application can persist its data.")

[Database Connection Configuration Details](database-connection-configuration-details-79d5638.md "Define details of the database connection used by your multitarget Java application in Cloud Foundry.")

[SAP HANA Cloud HDI Data Source](sap-hana-cloud-hdi-data-source-29639df.md "Set up HDI data sources for multitarget Java applications in SAP HANA Cloud.")

[TomEE Migration Guide \(Apache\)](http://help.sap.com/disclaimer?site=https://tomee.apache.org/developer/migration/tomee-1-to-7.html)

