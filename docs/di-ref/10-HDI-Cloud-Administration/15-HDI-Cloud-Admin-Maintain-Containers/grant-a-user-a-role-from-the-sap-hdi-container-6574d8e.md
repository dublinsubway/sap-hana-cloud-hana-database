<!-- loio6574d8eb496c4f2f9f023237abb6c87a -->

# Grant a User a Role from the SAP HDI Container's Schema

Use a role to enable access to an SAP HDI container's schema objects.



## Context

In SAP HANA Deployment Infrastructure \(HDI\), users who would like to consume objects deployed to an SAP HDI container \(for example, named “C”\) need to be granted the appropriate access privileges for the container's schema. The access privileges can be granted to specific objects in the schema \(for example, `C#DI`\) by use of a role that has been deployed to the container, or by granting privileges for the entire schema.

To grant privileges for specific objects in the container to a user `NEW_CONTAINER_CONSUMER` by use of a role in the target container, perform the following steps:



## Procedure

1.  In an SQL console, connect to the database with an administrator of the target HDI container \(for example, “C”\).

2.  Open the SQL editor for this database.

3.  Grant the role to the target user.

    Insert the following SQL code into the editor and adjust it to suit the requirements of your local environment:

    > ### Note:  
    > The temporary table `#ROLES` must be placed in a schema where the current user has the privileges required to create a temporary table.

    > ### Sample Code:  
    > ```sql
    > CREATE LOCAL TEMPORARY COLUMN TABLE #ROLES LIKE _SYS_DI.TT_SCHEMA_ROLES;
    > INSERT INTO #ROLES ( ROLE_NAME, PRINCIPAL_SCHEMA_NAME, PRINCIPAL_NAME ) VALUES ( 'myrole', '', 'NEW_CONTAINER_CONSUMER' );
    > CALL C#DI.GRANT_CONTAINER_SCHEMA_ROLES(#ROLES, _SYS_DI.T_NO_PARAMETERS, ?, ?, ?);
    > DROP TABLE #ROLES; 
    > ```

    1.  Adjust the name of the consumer user `NEW_CONTAINER_CONSUMER` in the `INSERT` statement in line 2 to reflect the name of the user to whom you want to assign the role.

    2.  Adjust the name of the role "`myrole`" in the `INSERT` statement in line 2 to reflect the name of the role you want to assign.

    3.  Adjust the schema name of the container C's API schema `C#DI` in the `CALL` statement in line 3.


4.  Execute the SQL code.

    Confirm that the SQL code completes successfully and displays the HDI return code 0.

5.  \(Optional\) Confirm that the `NEW_CONTAINER_CONSUMER` can now access the database objects specified by the role in the container's schema.


**Related Information**  


[Maintaining SAP HDI Containers](maintaining-sap-hdi-containers-bcd6e27.md "An HDI container administrator configures and controls access to a SAP HDI container.")

[Revoke a Role from the SAP HDI Container's Schema](revoke-a-role-from-the-sap-hdi-container-s-sch-bb47fc0.md "Use a role to disable access to an SAP HDI container's schema objects.")

