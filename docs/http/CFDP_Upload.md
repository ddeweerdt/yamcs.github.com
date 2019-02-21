---
layout: default
permalink: /docs/http/CFDP_Upload/
sidebar: yes
---
Upload, using the CFDP protocal, an object from a bucket to a remote CFDP entity:

    POST /api/cfdp/:instance/:bucketName/:objectName

<tt>_global</tt> can be used as instance name to refer to a bucket at the global level.

### Parameters

<table class="inline">
    <tr>
        <th>Name</th>
        <th>Type</th>
        <th>Description</th>
    </tr>
    <tr>
        <td class="code">target</td>
        <td class="code">string</td>
        <td>
            <strong>Required.</strong> The destination path and filename (eg: a/local/path/some_filename) at the remote CFDP entity.
        </td>
    </tr>
    <tr>
	<td class="code">overwrite</td>
	<td class="code">boolean</td>
	<td>Set to <tt>True</tt> if an already existing destination should be overwritten. Default: <tt>True</tt></td>
    </tr>
    <tr>
	<td class="code">createpath</td>
	<td class="code">boolean</td>
	<td>Set to <tt>True</tt> if the destination path should be created if it does not exist. Default: <tt>True</tt></td>
    </tr>
</table>

### Response

<pre class="header">Status: 200 OK</pre>

```json
{
  "transfer_id": 1
}
```
