---
layout: default
permalink: /docs/http/CFDP_Get_Info/
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
	"transfer_id": 1,
  	"instance_name": "my_instance",
  	"bucket_name": "my_bucket",
  	"object_name": "my_object",
  	"remote_filepath": "a/remote/path/filename",
  	"upload_download": "upload",
  	"completion": "49%",
  	"state": "ongoing, stalled"
  },
  {
	"transfer_id": 2,
	"instance_name": "my_instance",
	"bucket_name": "some_bucket",
	"object_name": "some_object",
	"remote_filepath": "a/remote/path/other_filename",
	"upload_download": "download",
	"completion": "5%",
	"state": "finished, aborted"
  },
  {
	"transfer_id": 3,
	"instance_name": "my_instance",
	"bucket_name": "some_bucket",
	"object_name": "some_object",
	"remote_filepath": "a/remote/path/other_filename",
	"upload_download": "download",
	"completion": "100%",
	"state": "finished, completed"
  }
}
```


