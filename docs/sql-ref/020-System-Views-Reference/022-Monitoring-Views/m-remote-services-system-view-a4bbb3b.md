<!-- loioa4bbb3b6d2e246d8bf4938f7c9c413b2 -->

# M\_REMOTE\_SERVICES System View

Provides information on outbound connectivity status to external SAP-managed services running in SAP HANA cloud.



## Structure


<table>
<tr>
<th valign="top">

Column name



</th>
<th valign="top">

Data type



</th>
<th valign="top">

Description



</th>
</tr>
<tr>
<td valign="top">

HOST



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the host name.



</td>
</tr>
<tr>
<td valign="top">

PORT



</td>
<td valign="top">

INTEGER



</td>
<td valign="top">

Displays the internal port.



</td>
</tr>
<tr>
<td valign="top">

SERVICE\_NAME



</td>
<td valign="top">

NVARCHAR\(64\)



</td>
<td valign="top">

Displays the service name.



</td>
</tr>
<tr>
<td valign="top">

ACTIVE\_STATUS



</td>
<td valign="top">

NVARCHAR\(16\)



</td>
<td valign="top">

Displays the service status.



</td>
</tr>
<tr>
<td valign="top">

REQUEST\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the count of requests that SAP HANA database sent to the remote service.



</td>
</tr>
<tr>
<td valign="top">

FAILED\_REQUEST\_COUNT



</td>
<td valign="top">

BIGINT



</td>
<td valign="top">

Displays the count of unsuccessful requests that SAP HANA database sent to the remote service.



</td>
</tr>
<tr>
<td valign="top">

LAST\_REQUEST\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the last timestamp that SAP HANA database made a request to the remote service and received a success response.



</td>
</tr>
<tr>
<td valign="top">

LAST\_ERROR\_TIME



</td>
<td valign="top">

TIMESTAMP



</td>
<td valign="top">

Displays the last timestamp that SAP HANA database received an error from the remote service or a connection failed.



</td>
</tr>
<tr>
<td valign="top">

LAST\_ERROR\_CODE



</td>
<td valign="top">

INT



</td>
<td valign="top">

Displays the last error code that SAP HANA database received from the remote service or was internally generated by SAP HANA database.



</td>
</tr>
<tr>
<td valign="top">

LAST\_ERROR\_MESSAGE



</td>
<td valign="top">

NVARCHAR\(5000\)



</td>
<td valign="top">

Displays the last error message that SAP HANA database received from the remote service or was internally generated by SAP HANA database.



</td>
</tr>
</table>

