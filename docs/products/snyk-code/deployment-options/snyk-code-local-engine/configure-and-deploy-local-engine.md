# Configure and deploy Local Engine

### Installing the Helm Chart

To install the chart with the release name `my-release`:

```
$ helm install my-release <gziped-chart>
```

These commands deploy `local-code-engine` on the Kubernetes cluster in the default configuration. The **Parameters** section lists the parameters that can be configured during installation.

To print the default values file of the chart run:

```
$ helm show values <gziped-chart>
```

#### Uninstalling the Helm Chart

To uninstall/delete the my-release resources:

```
$ helm delete my-release
```

The command removes all the Kubernetes components associated with the chart and deletes the release. Use the option `--purge` to delete all history too.

### Global Parameters

#### Global Required parameters

| Name                                          | Description                  | Default Value |
| --------------------------------------------- | ---------------------------- | ------------- |
| `global.imagePullSecret.credentials.username` | Docker hub registry username | `""`          |
| `global.imagePullSecret.credentials.password` | Docker hub registry password | `""`          |

#### Broker required parameters

Please use _one_ of the following SCM configurations:

| Name                        | Description                                                                                                           | Default Value |
| --------------------------- | --------------------------------------------------------------------------------------------------------------------- | ------------- |
| `broker-client.brokerToken` | Unique broker client token                                                                                            | `""`          |
| `broker-client.brokerType`  | Type of broker client to use. supported options: github-com, github-enterprise, gitlab, bitbucket-server, azure-repos | `""`          |

#### GitHub.com parameters

| Name                        | Description                                      | Default Value |
| --------------------------- | ------------------------------------------------ | ------------- |
| `broker-client.githubToken` | Token for [http://github.com](http://github.com) | `""`          |

#### GitHub Enterprise parameters

| Name                          | Description                                      | Default Value                                     |
| ----------------------------- | ------------------------------------------------ | ------------------------------------------------- |
| `broker-client.githubToken`   | Token for [http://github.com](http://github.com) | `""`                                              |
| `broker-client.githubHost`    | Host name for GitHub server                      | `""`                                              |
| `broker-client.githubApi`     | GitHub REST API url, excluding scheme            | `"{{ .Values.broker-client.githubHost }}/api/v3"` |
| `broker-client.githubGraphql` | GitHub GraphQL API url, excluding scheme         | `"{{ .Values.broker-client.githubHost }}/api"`    |

#### Gitlab parameters

| Name                        | Description                 | Default Value |
| --------------------------- | --------------------------- | ------------- |
| `broker-client.gitlabToken` | gitlab Host                 | `""`          |
| `broker-client.gitlabHost`  | Host name for gitlab server | `""`          |

#### Bitbucket server parameters

| Name                              | Description                    | Default Value |
| --------------------------------- | ------------------------------ | ------------- |
| `broker-client.bitbucketUsername` | bitbucket username             | `""`          |
| `broker-client.bitbucketPassword` | bitbucket password             | `""`          |
| `broker-client.bitbucketHost`     | Host name for bitbucket server | `""`          |

#### Azure Repos parameters

| Name                            | Description               | Default Value |
| ------------------------------- | ------------------------- | ------------- |
| `broker-client.azureReposToken` | Token for Azure Repos     | `""`          |
| `broker-client.azureReposHost`  | Host name for Azure Repos | `""`          |
| `broker-client.azureReposOrg`   | Azure organization name   | `""`          |

### Snyk Code Local Engine Parameters

#### codeapi

| Name                                 | Description                                                                           | Default Value |
| ------------------------------------ | ------------------------------------------------------------------------------------- | ------------- |
| `codeapi.imagePullSecrets`           | Docker registry secret names as an array                                              | `[]`          |
| `codeapi.nameOverride`               | String to partially override names.fullname template (will maintain the release name) | `""`          |
| `codeapi.fullnameOverride`           | String to fully override names.fullname template                                      | `""`          |
| `codeapi.serviceAccount.create`      | Specify whether a ServiceAccount should be created                                    | `true`        |
| `codeapi.serviceaccount.name`        | The name of the ServiceAccount to create                                              | `""`          |
| `codeapi.serviceAccount.annotations` | Additional Service Account annotations (evaluated as a template)                      | `{}`          |
| `codeapi.podAnnotations`             | Pod annotations                                                                       | `{}`          |
| `codeapi.podSecurityContext`         | security context for pod                                                              | `{}`          |
| `codeapi.securityContext`            | holds security configuration that will be applied to a container                      | `{}`          |
| `codeapi.nodeSelector`               | Aggregator Node labels for pod assignment                                             | `{}`          |
| `codeapi.tolerations`                | Aggregator Tolerations for pod assignment                                             | `[]`          |
| `codeapi.affinity`                   | Forwarder Affinity for pod assignment                                                 | `{}`          |

#### bundle

| Name                                   | Description                                                                           | Default Value |
| -------------------------------------- | ------------------------------------------------------------------------------------- | ------------- |
| `bundle.imagePullSecrets`              | Docker registry secret names as an array                                              | `[]`          |
| `bundle.nameOverride`                  | String to partially override names.fullname template (will maintain the release name) | `""`          |
| `bundle.fullnameOverride`              | String to fully override names.fullname template                                      | `""`          |
| `bundle.serviceAccount.create`         | Specify whether a ServiceAccount should be created                                    | `true`        |
| `bundle.serviceaccount.name`           | The name of the ServiceAccount to create                                              | `""`          |
| `bundle.serviceAccount.annotations`    | Additional Service Account annotations (evaluated as a template)                      | `{}`          |
| `bundle.podAnnotations`                | Pod annotations                                                                       | `{}`          |
| `bundle.podSecurityContext`            | security context for pod                                                              | `{}`          |
| `bundle.securityContext`               | holds security configuration that will be applied to a container                      | `{}`          |
| `bundle.nodeSelector`                  | Aggregator Node labels for pod assignment                                             | `{}`          |
| `bundle.tolerations`                   | Aggregator Tolerations for pod assignment                                             | `[]`          |
| `bundle.affinity`                      | Forwarder Affinity for pod assignment                                                 | `{}`          |
| `bundle.terminationGracePeriodSeconds` | Duration in seconds the pod needs to terminate gracefully                             | `10`          |

#### suggest

| Name                                 | Description                                                                           | Default Value |
| ------------------------------------ | ------------------------------------------------------------------------------------- | ------------- |
| `suggest.imagePullSecrets`           | Docker registry secret names as an array                                              | \`\[]         |
| `suggest.nameOverride`               | String to partially override names.fullname template (will maintain the release name) | `""`          |
| `suggest.fullnameOverride`           | String to fully override names.fullname template                                      | `""`          |
| `suggest.serviceAccount.create`      | Specify whether a ServiceAccount should be created                                    | `true`        |
| `suggest.serviceaccount.name`        | The name of the ServiceAccount to create                                              | `""`          |
| `suggest.serviceAccount.annotations` | Additional Service Account annotations (evaluated as a template)                      | `{}`          |
| `suggest.podAnnotations`             | Pod annotations                                                                       | `{}`          |
| `suggest.podSecurityContext`         | security context for pod                                                              | `{}`          |
| `suggest.securityContext`            | holds security configuration that will be applied to a container                      | `{}`          |
| `suggest.nodeSelector`               | Aggregator Node labels for pod assignment                                             | `{}`          |
| `suggest.tolerations`                | Aggregator Tolerations for pod assignment                                             | `[]`          |
| `suggest.affinity`                   | Forwarder Affinity for pod assignment                                                 | `{}`          |

#### broker-client

| Name                                       | Description                                                                           | Default Value |
| ------------------------------------------ | ------------------------------------------------------------------------------------- | ------------- |
| `broker-client.codeSnippet.enabled`        | Enable code Snippets                                                                  | `false`       |
| `broker-client.imagePullSecrets`           | Docker registry secret names as an array                                              | `[]`          |
| `broker-client.nameOverride`               | String to partially override names.fullname template (will maintain the release name) | `""`          |
| `broker-client.fullnameOverride`           | String to fully override names.fullname template                                      | `""`          |
| `broker-client.serviceAccount.create`      | Specify whether a ServiceAccount should be created                                    | `true`        |
| `broker-client.serviceaccount.name`        | The name of the ServiceAccount to create                                              | `""`          |
| `broker-client.serviceAccount.annotations` | Additional Service Account annotations (evaluated as a template)                      | `{}`          |
| `broker-client.podAnnotations`             | Pod annotations                                                                       | `{}`          |
| `broker-client.podSecurityContext`         | security context for pod                                                              | `{}`          |
| `broker-client.securityContext`            | holds security configuration that will be applied to a container                      | `{}`          |
| `broker-client.nodeSelector`               | Aggregator Node labels for pod assignment                                             | `{}`          |
| `broker-client.tolerations`                | Aggregator Tolerations for pod assignment                                             | `[]`          |
| `broker-client.affinity`                   | Forwarder Affinity for pod assignment                                                 | `{}`          |

### Third-party charts

If you want to configure some of the third-party services that we use, examples can be found here:

* [Ambassador](https://github.com/emissary-ingress/emissary/tree/master/charts/emissary-ingress)
* [Redis](https://github.com/bitnami/charts/tree/master/bitnami/redis)
* [Fluentd](https://github.com/bitnami/charts/tree/master/bitnami/fluentd)

### Chart Usage

You can edit the provided YAML file according to your needs.

Alternatively, you can use your own YAML file that specifies the values for the parameters can be provided while installing the chart. For example,

`$ helm install my-release -f your-values.yaml`

### Logging

Fluentd is used to aggregate all our services' logs into one file.

The log file is rotated daily unless the file exceeded `fluentd-umbrella.logrotate.fileMaxSizeInMb` (default 500) and the number of files logrotate keeps is `fluentd-umbrella.logrotate.filesToKeep` (default 14). So a log file for the whole day is generated only the day after, unless it exceeds `fileMaxSizeInMb`.

Logrotate validates that the number of log files is not above `fluentd-umbrella.logrotate.filesToKeep` by removing the oldest log file when the number of log files is equal to `filesToKeep`+1 files.

When a file is rotated, the date and time of rotation is added as a suffix to the file name. To see the current logs, you must tail the `code.log` file. To fetch logs written in the past, pick the log file with date and time after the timeframe you want to see.

To fetch all log files to current directory, run:

```
kubectl cp <your-namespace>/<your-release>-fluentd-0:/var/log/snyk/logs ./
```

To fetch log files for specific dates first get exsiting logs list, run:

```
kubectl exec -it on-prem-fluentd-0 -- ls -l /var/log/snyk/logs
```

Then copy the log file you want to fetch by running:

```
kubectl cp <your-namespace>/<your-release>-fluentd-0:/var/log/snyk/logs/<file-name> ./<target-file-name>
```

{% hint style="info" %}
It may take a few minutes to copy all files.
{% endhint %}

### Enabling webhooks for broker client for Snyk Code PR Scanning

In order to be able to create and handle SCM webhooks, `broker-client` must be exposed to the outside world.&#x20;

A basic ingress is available for it and can be enabled by setting `broker-client.ingress.enabled` to `true` and specifying a host on which the broker client's endpoints will be available via `broker-client.ingress.host` (for example "broker-client.example.com"). The default ingress exposes `/webhook/*` and `/healthcheck` endpoints from the `broker-client` service.

Note that the ingress IP still has to be made available on the specified host via a DNS A record, which will depend on your cloud provider or server setup.

By default, the ingress endpoints are insecure. In order to secure them using TLS, set `broker-client.ingress.tls.enabled` to `true`.

You can specify the name of the secret you wish to use with `broker-client.ingress.tls.secret.name`, or leave it empty to default to the name of the service suffixed with `-tls-secret`.

If you do not already have a secret created for that host, you can set the `key` and `cert` values to the key and certificate, respectively, that you created for use with the host that the ingress will be using (they will be Base64 encoded for you

Read more about securing an ingress with TLS [here](https://kubernetes.io/docs/concepts/services-networking/ingress/#tls).\
\
