---
layout: default
permalink: /docs/http/CFDP_Download/
sidebar: yes
---
Download, using the CFDP protocol, a file from a remote CFDP entity to an object in a bucket:

    GET /api/cfdp/:instance/:bucketName/:objectName

<tt>_global</tt> can be used as instance name to refer to a bucket at the global level.

If the bucketName is <tt>user.username</tt> then a bucket will be created automatically if it does not exist. Otherwise the bucket must exist before being download to.

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
            <strong>Required.</strong> The source path and filename (eg: a/local/path/some_filename) at the remote CFDP entity.
        </td>
    </tr>
    <tr>
	<td class="code">overwrite</td>
	<td class="code">boolean</td>
	<td>Set to <tt>True</tt> if an already existing <tt>objectName</tt> should be overwritten. Default: <tt>True</tt></td>
    </tr>
</table>

### Response

<pre class="header">Status: 201 Created</pre>

```json
{
  "transfer_id": 1
}
```

