<!---
  Licensed to the Apache Software Foundation (ASF) under one
  or more contributor license agreements.  See the NOTICE file
  distributed with this work for additional information
  regarding copyright ownership.  The ASF licenses this file
  to you under the Apache License, Version 2.0 (the
  "License"); you may not use this file except in compliance
  with the License.  You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

  Unless required by applicable law or agreed to in writing,
  software distributed under the License is distributed on an
  "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
  KIND, either express or implied.  See the License for the
  specific language governing permissions and limitations
  under the License.
-->

qbt
===

`qbt` is a command to execute test-patch without a patch.  It uses
the same plug-ins and the same options as test-patch.  The only
difference is that no patch file, location, etc should be supplied.
It is meant to be a way to easily get test-patch's output on your
current source tree.  It is suitable to be run as a regularly
scheduled build as part of your overall development strategy.

When using an automation tool, it may be useful to use the
`--console-report-file` option to send the summary email to a
file. This can then be used with systems like Jenkin's
email-ext plug-in to send the output as an emailed report:

```
${FILE,path="<report-file-path>"}
```

For something a bit more structured, there is also the `--html-report-file`
option.  Using this output, again with Jenkins' email-ext plug-in, it is
possible to build some very nice looking output that is easily customized:

```
<html>
<head>
<style>
table {
    border-collapse: collapse;
}
table, th, td {
   border: 1px solid black;
}
tr:nth-child(even){background-color: #f2f2f2}
</style>
</head>
<body>
<p>See the <a href="${BUILD_URL}">Jenkins Build</a> for more information.</p>
<p>${CHANGES, format="<div>[%d] (%a) %m</div>"}</p>
<p></p>
${FILE,path="<report-file-path>"}
</body></html>
```

NOTE: Be aware that ASF mailing lists do not allow HTML formatted email.
