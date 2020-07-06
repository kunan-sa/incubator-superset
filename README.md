<!--
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
Superset
=========

<img
  src="https://cloud.githubusercontent.com/assets/130878/20946612/49a8a25c-bbc0-11e6-8314-10bef902af51.png"
  alt="Superset"
  width="500"
/>

#Login through token

## Introduction
In this branch of the fork Superset was modified in order to implement
a solution to the login through token problem. This makes it available
to embed a dashboard or a chart in a web application, skipping the
login screen, and to use the web api's login logic in Superset.

## Changes made
In order to achieve this a Custom Superset Security Manager was added,
which overrides Superset's Security Manager in the case a token is passed
through params, for example:

```
<superset-endpoint>/login/?token=a
```
in order to do this, an api must be running and its endpoint must be added
to the **superset/config.py** file.

We provide an example api, to show how such api would look like.

### Modified files
* `superset/security/__init__.py`
* `superset/config.py`

### Added files
* `login-api/api.py`
* `superset/security/security.py`

## Installation
In order to run this, superset must be installed as a development env.
Please follow the [official documentation](https://github.com/apache/incubator-superset/blob/master/CONTRIBUTING.md#flask-server)
