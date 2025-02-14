<!-- loio20d5412b75191014bc7ec7e133ce5bf5 -->

# CREATE SYNONYM Statement \(Data Definition\)

Creates an alternate name for a table, view, procedure, or sequence.



<a name="loio20d5412b75191014bc7ec7e133ce5bf5__sql_create_synonym_1sql_create_synonym_syntax"/>

## Syntax

```
CREATE [ OR REPLACE ] [ PUBLIC ] SYNONYM <synonym_name> FOR <synonym_source_object_name>
```



<a name="loio20d5412b75191014bc7ec7e133ce5bf5__sql_create_synonym_1sql_create_synonym_syntax_elements"/>

## Syntax Elements


<dl>
<dt><b>

OR REPLACE

</b></dt>
<dd>

Replaces the definition of the synonym if it already exists. A CREATE OR REPLACE operation does not change the ID of the synonym, nor any privileges associated with it.



</dd><dt><b>

*<synonym\_name\>*

</b></dt>
<dd>

Specifies the name of the synonym to be created, with optional schema name.

```
<synonym_name> ::= [ <schema_name>.]<identifier>

<schema_name> ::= <unicode_name>
```

When you create a synonym for PUBLIC, you cannot specify a schema name \(*<schema\_name\>*\).



</dd><dt><b>

*<synonym\_source\_object\_name\>*

</b></dt>
<dd>

Specifies the object you are creating a synonym for.

```
<synonym_source_object_name> ::=
 <table_name>
 | <view_name>
 | <procedure_name>
 | <sequence_name>

<table_name> ::= [ [ <database_name>.]<schema_name>.]<identifier>
<view_name> ::= [ <schema_name>.]<identifier>
<sequence_name> ::= [ <schema_name>.]<identifier>
<procedure_name> ::= [ <schema_name>.]<identifier>
 
<database_name> ::= <identifier>
<schema_name> ::= <unicode_name>
```

*<database\_name\>* can only be applied to tables and views, not to sequences or procedures.

The *<database\_name\>* syntax can be used only in a system with multiple database containers where cross-database access is enabled for the given database name.

For linked database, *<database\_name\>* is the name of the remote source. *<identifier\>* is the name of the table on the remote source.



</dd>
</dl>



<a name="loio20d5412b75191014bc7ec7e133ce5bf5__sql_create_synonym_1sql_create_synonym_description"/>

## Description

Use a synonym to re-point functions and stored procedures to differing tables, views, or sequences without rewriting the function or stored procedure.

The optional PUBLIC element allows you to create a public synonym.



<a name="loio20d5412b75191014bc7ec7e133ce5bf5__section_k25_zdh_qbb"/>

## Permissions

No additional privilege is required to create a synonym on an object within your own schema. The CREATE ANY object privilege is required to create synonym on an object within another user's schema.

Any user can access a public synonym, but only the users that have the proper privileges on its base object can access the base object.



<a name="loio20d5412b75191014bc7ec7e133ce5bf5__sql_create_synonym_1sql_create_synonym_examples"/>

## Example

Create table A.

```
CREATE ROW TABLE A (A INT PRIMARY KEY, B INT);
```

Create a synonym for table A, a\_synonym.

```
CREATE SYNONYM a_synonym FOR A;
```

