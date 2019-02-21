---
layout: default
permalink: /docs/http/CFDP_Cancel/
sidebar: yes
---
Cancel one, more or all ongoing CFDP transfer: 

    POST /api/cfdp/cancel

The ongoing transfer will be aborted, the partially uploaded/downloaded file is retained.

### Parameters

<table class="inline">
	<tr>
		<th>Name</th>
		<th>Type</th>
		<th>Description</th>
	</tr>
        <tr>
                <td class="code">transaction ids</td>
                <td class="code">array of integers</td>
                <td>an optional list of CFDP transfer ids that have to be cancelled (if not cancelled/finished already). If this parameter is absent, all ongoing CFDP transfers are cancelled.</td>
        </tr>
</table>

### Response

<pre class="header">Status: 200 OK</pre>

```json
{
  "cancelled_transfers": [3, 5, 9] 
}
```
