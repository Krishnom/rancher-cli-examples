# Rancher CLI Usage

## Example commands to operate rancher right from commandline on any machine.

## Prerequisites
While most of the stuffs are documented at [rancher-cli][rancher-cli-doc] (and it will work almost everytime) , This document contains any issue that you might while using the rancher's cli.

So what you need in all ?
  - Windows/Linux/MacOs
  - Rancher CLI binary for you host [rancher-cli-download][rancher-cli-binary]
  - kubectl for firing containers in rancher [installing-kubectl][install-kubectl]
  - Bearer Token [generate token][How Generating Bearer Token]
  > Please use "no-scope" while creating API for user. [see this issue][rancher-apitoken-scoped-to-cluser-ssue]
  

> Assuming your rancher-cli binary is at /usr/bin/rancher
## Login
`/usr/bin/rancher login https://<SERVER_URL> --token <BEARER_TOKEN>`

> Accept the Insecure PKI key prompt when asked. Select the context from the list of the context

Alternatively, To run command without any user interaction. 
> For below command you need PROJECT_ID. To retrieve it, you can checkout output of https://<SERVER_URL>/v3/projects?sort=description. Check the "data" field in the json and you will get all the projects details in it. The "id" field is what your project id will be. Check the "name" field to cross verify your project

`/usr/bin/rancher login https://<SERVER_URL> --token <BEARER_TOKEN> --skip-verify --context <PROJECT_ID>`

## List of running containers/jobs/workload
`/usr/bin/rancher ps`

## Running a job
`/usr/bin/rancher kubectl apply -f <yaml file>`
> For yaml file sample, checkout [nginx-deployment][sample-yaml-file]

## Deleting the job
`/usr/bin/rancher kubectl delete -f <yaml file>`









[How Generating Bearer Token]: <https://rancher.com/docs/rancher/v2.x/en/user-settings/api-keys/#creating-an-api-key>
[rancher-cli-binary]: <https://github.com/rancher/cli/releases>
[install-kubectl]: <https://kubernetes.io/docs/tasks/tools/install-kubectl>
[rancher-cli-doc]: <https://rancher.com/docs/rancher/v2.x/en/cli/>
[rancher-apitoken-scoped-to-cluser-ssue]: <https://github.com/rancher/rancher/issues/19348>
[sample-yaml-file]: <https://raw.githubusercontent.com/kubernetes/website/master/content/en/examples/controllers/nginx-deployment.yaml>
