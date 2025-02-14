<!-- loio4924523ccf5d4c56bd414f6eb9e08efa -->

# PUBLIC\_KEYS System View

Provides information about all public keys.



<a name="loio4924523ccf5d4c56bd414f6eb9e08efa__section_pnq_ynd_tfb"/>

## Structure


<table>
<tr>
<th valign="top">

Column Name



</th>
<th valign="top">

Data Type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

PUBLIC\_KEY\_NAME



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays a unique name of the public key



</td>
</tr>
<tr>
<td valign="top">

ALGORITHM



</td>
<td valign="top">

CHAR\(3\)



</td>
<td valign="top">

Displays the algorithm of this key \(RSA or EC\)



</td>
</tr>
<tr>
<td valign="top">

ALGORITHM\_DETAILS



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the keysize for RSA or the used curve for EC



</td>
</tr>
<tr>
<td valign="top">

KEY



</td>
<td valign="top">

NVARCHAR\(5000\)



</td>
<td valign="top">

Displays the PEM representation of the key \(PKCS1 or PKCS8\)



</td>
</tr>
<tr>
<td valign="top">

KEY\_ID\_HINT



</td>
<td valign="top">

NVARCHAR\(256\)



</td>
<td valign="top">

Displays the hint ID this key has in an external key management system \(e.g. JWKS\)



</td>
</tr>
<tr>
<td valign="top">

COMMENT



</td>
<td valign="top">

NVARCHAR\(1024\)



</td>
<td valign="top">

Displays the description for the key



</td>
</tr>
<tr>
<td valign="top">

CREATE\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the creation timestamp of the public key in the database



</td>
</tr>
</table>



<a name="loio4924523ccf5d4c56bd414f6eb9e08efa__section_bbs_ppd_tfb"/>

## Permissions

For information on the permissions required to use this view, see *SQL Statements and Authorization for Certificate Management \(Reference\)*.

**Related Information**  


[SQL Statements and Authorization for Certificate Management (Reference)](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/2023_2_QRC/en-US/f32bcc9c4b734f24bedaf6253e7981d6.html "All administration tasks related to the management of public-key certificates (and public keys) can be performed using SQL.") :arrow_upper_right:

[PSE\_PURPOSE\_OBJECTS System View](pse-purpose-objects-system-view-437cd32.md "Provides information about all PSEs and their assigned providers or hosts, referred to as purpose objects.")

