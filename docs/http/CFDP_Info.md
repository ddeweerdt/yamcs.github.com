---
layout: default
permalink: /docs/http/CFDP_Info/
sidebar: yes
---
Get info on one, multiple or all ongoing and/or finished/cancelled CFDP transfers:

    GET /api/cfdp/info

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
		<td>an optional list of CFDP transfer ids whereof the info is to be returned</td>
	</tr>
	<tr>
		<td class="code">all</td>
		<td class="code">boolean</td>
		<td>If set to <tt>True</tt>, info for all current and past CFDP transfers is shown. If set to <tt>False</tt>, only ongoing CFDP transfers are considered. Ignored if <tt>transaction ids</tt> is present. Default: <tt>True</tt></td>
	</tr>
</table>

### Response

<pre class="header">Status: 200 OK</pre>

```json
{
  "transfers": [ {
	"transferId": 1,
  	"instanceName": "my_instance",
  	"bucketName": "my_bucket",
  	"objectName": "my_object",
  	"remoteFilepath": "a/remote/path/filename",
  	"uploadDownload": "upload",
  	"completion": "49%",
  	"state": "ongoing, stalled"
  },
  {
	"transferId": 2,
	"instanceName": "my_instance",
	"bucketName": "some_bucket",
	"objectName": "some_object",
	"remoteFilepath": "a/remote/path/other_filename",
	"uploadDownload": "download",
	"completion": "5%",
	"state": "finished, aborted"
  },
  {
	"transferId": 3,
	"instanceName": "my_instance",
	"bucketName": "some_bucket",
	"objectName": "some_object",
	"remoteFilepath": "a/remote/path/other_filename",
	"uploadDownload": "download",
	"completion": "100%",
	"state": "finished, completed"
  }
}
```


