# Node-Red Setup

Open-ITDR contains an implementation reference for security automation tasks. Those flows include:
1. Secret and configuration initialization workflow
2. Upon a trigger (Webhook or anything else), sending a customized email that contains a link to a customized landing page. The landing page allows the user to respond to a question with a Yes/No response, and the flows continues according to the decision of the user. This flow is useful for cases where the response of a user is requested, for example if we find a user is inactive for a while, the flow can be configured to query the manager of the user if that user account can be suspended, and automatically close the account in case they approve it.
3. Sample interacting with the Authomize platform - updating incidents, fetching more info
4. A simple email sending flow

## Recommended Setup

Node-Red is the platform of choice for Open-ITDR. It is recommended to choose a PaaS vendor such as [Stackhero](https://www.stackhero.io/en/services/Node-RED/documentations/Getting-started) to setup an instance of Node-Red without the maintenance burden. PaaS vendors limit access to the Node-Red machine (such as disabling access to the `settings.js` file). This repo provides key tools to build a security-oriented workflow engine on top of Node-Red, under the assumption of using such a PaaS provider. The architecture of the recommended deployment is as follows:

1. Secrets - required in order to integrate to 3rd party services. Secrets will be manually configured once using a[node-red-contrib-credentials](https://flows.nodered.org/node/node-red-contrib-credentials) Credentials node. The node will be configured to keep values in the global context, so that those values are available to other nodes.
2. A local sqlite DB ([node-red-node-sqlite](https://flows.nodered.org/node/node-red-node-sqlite)) used to keep track of communication flows that involve a response of a user via Email/Slack.
3. Configuration flow that is initialized upon startup, and initiates everything (secrets, DB and anything else).

### Required Packages
* [node-red-contrib-credentials](https://flows.nodered.org/node/node-red-contrib-credentials)
* [node-red-node-sqlite](https://flows.nodered.org/node/node-red-node-sqlite)

### Setup Steps
1. Import the following flows:
   1. ...
