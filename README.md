# unraid-templates
Storage for Unraid App templates incl. icons

# 🔑 License
This repository is under  GNU GENERAL PUBLIC LICENSE Version 3, 29 June 2007 -> See [License](https://raw.githubusercontent.com/chrizzo84/unraid-templates/main/LICENSE?token=GHSAT0AAAAAABXMPMKOUPLGTE3ONEXO7B7KYZSSXZQ)

---
---
# ⚓ Table of contents
1. [Drone CI Gitea](#Drone)
2. [Azure DevOps Pipelines Agent](#Agent)
3. [Issues](#Issues)
---
---

<div id='Drone'/>

## ⚒️ Drone CI Gitea
The Drone CI template is specially designed for use with Gitea.

### Description:
Drone by [Harness™](https://harness.io/) is a modern Continuous Integration platform that empowers busy teams to automate their build, test and release workflows using a powerful, cloud native pipeline engine. ([Source](https://docs.drone.io)) 

Link to Drone Documentation: https://docs.drone.io

### Variables:
| **Variablename**          | **Required** | **Description**                                                                                                                                                                                                    | **Default**              |
|---------------------------|--------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|--------------------------|
| HTTP_PORT                 | X            | Container HTTP Port                                                                                                                                                                                                | 9080                     |
| HTTPS_PORT                | X            | Container HTTPS Port                                                                                                                                                                                               | 9443                     |
| DRONE_AGENTS_ENABLED      | X            | Set to true if you want to run server and agent in the same container.                                                                                                                                             | false                    |
| DRONE_GITEA_SERVER        | X            | Gitea Server URL                                                                                                                                                                                                   | empty                    |
| DRONE_GITEA_CLIENT_ID     | X            | Needs to be generated in Gitea -> More info: https://docs.drone.io/server/provider/gitea/                                                                                                                          | empty                    |
| DRONE_GITEA_CLIENT_SECRET | X            | Needs to be generated in Gitea -> More info: https://docs.drone.io/server/provider/gitea/                                                                                                                          | empty                    |
| DRONE_RPC_SECRET          | X            | Create a shared secret to authenticate communication between runners and your central Drone server. Use "openssl rand -hex 16" to generate a key                                                                   | empty                    |
| DRONE_SERVER_HOST         | X            | Your Drone Server URL                                                                                                                                                                                              |                          |
| DRONE_SERVER_PROTO        | X            | Required string value configures the user-facing protocol. This value is used to create webhooks and redirect urls. It has no actual impact on serving traffic. Possible values are "http" or "https".             | empty                    |
| DRONE_GIT_ALWAYS_AUTH     | X            | Optional boolean value. Configures Drone to authenticate when cloning public repositories. This is only required when your source code management system (e.g. GitHub Enterprise) has private mode enabled.        | true                     |
| DRONE_USER_CREATE         | X            | Optional user account that should be created on startup. This should be used to seed the system with an administrative account. It can be a real account (i.e. a real GitHub user) or it can be a machine account. | username:root,admin:true |



---
---
<div id='Agent'/>

## 🔩 Azure DevOps Pipelines Agent
Ubuntu 22.04 Azure Pipelines Agent with some preinstalled software.

### Preinstalled Software:
- OpenJDK17
- OpenJDK11
- OpenJDK 8
- Dotnet 6
- Python3

### Capabilities:
| **Env**              | **Path**                                |
|------------------|-------------------------------------|
| curl             | /usr/bin/curl                       |
| dotnet           | /usr/bin/dotnet                     |
| git              | /usr/bin/git                        |
| JAVA_HOME_11_X64 | /usr/lib/jvm/java-11-openjdk-amd64  |
| JAVA_HOME_17_X64 | /usr/lib/jvm/java-17-openjdk-amd64  |
| JAVA_HOME_8_X64  | /usr/lib/jvm/java-8-openjdk-amd64   |
| python3          | /usr/bin/python3                    |

### Variables:
| **Variablename** | **Description**                                                                                |
|------------------|------------------------------------------------------------------------------------------------|
| AZP_URL          | Azure DevOps URL                                                                               |
| AZP_TOKEN        | Personal Access Token                                                                          |
| AZP_AGENT_NAME   | Name of the Agent                                                                              |
| AZP_POOL         | Azure DevOps Agent Pool Name - If not filled out Agent will be installed to Default Agent Pool |
| AZP_WORK         | Work folder (default = _work)


### Use Docker within Docker container
Please bind-mount Docker socket.

---
---
<div id='Issues'/>

# ⚠️ Issues: <a name="Issues"></a>
If you have any issues please create new Issue [here](https://github.com/chrizzo84/unraid-templates/issues) Tag [Drone].
For example: [Drone] My Problem or [AzPipeline] My Problem

**Please only open issues here that are directly related to the Unraid App template or similar.**


