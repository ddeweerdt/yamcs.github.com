---
layout: default
permalink: /docs/http/CFDP_Delete/
sidebar: yes
---
Removes an item in a path on the remote CFDP entity:

    POST /api/cfdp/delete

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
            <strong>Required.</strong> The target filepath at the remote CFDP entity.
        </td>
    </tr>
</table>

### Response

<pre class="header">Status: 200 OK</pre>
