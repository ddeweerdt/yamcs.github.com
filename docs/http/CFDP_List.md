---
layout: default
permalink: /docs/http/CFDP_List/
sidebar: yes
---
Get the contents of a path on the remote CFDP entity, using the CFDP protocol:

    GET /api/cfdp/list

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
            <strong>Required.</strong> The target path at the remote CFDP entity.
        </td>
    </tr>
</table>

### Response

<pre class="header">Status: 200 OK</pre>

```json
{
  "remotePath": "a/remote/path",
  "items": [ {
	"name": "a_file",
	"isDirectory": False
  },
  {
	"name": "a_directory",
	"isDirectory": True
  }
}
```


