# Azure Container Instances Samples
Deploy Containerized Microservices to Azure Container Instances

## Deploy the container group

Create a resource group with the `az group create` command:

```sh
$ az group create --name aciSamples --location eastus
```

Deploy the container group with the `az container create` command, passing the YAML file as an argument:

```sh
$ az container create --resource-group aciSamples --file voting-app-deploy.yaml
```

## View deployment state

To view the state of the deployment, use the following `az container show` command:

```sh
$ az container show --resource-group aciSamples --name aciVotingApp --output table
```

## View container logs

View the log output of a container using the `az container logs` command. The `--container-name` argument specifies the container from which to pull logs. In this example, the `voting-frontend` container is specified.

```sh
$ az container logs --resource-group aciSamples --name aciVotingApp --container-name voting-frontend
```

## Cleanup

Delete the container group with the `az container delete` command:

```sh
$ az container delete --resource-group aciSamples --name aciVotingApp
```

Delete the resource group with the `az group delete` command:

```sh
$ az group delete --name aciSamples
```