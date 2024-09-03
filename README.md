# yCrash Helm Charts

[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)
[![Version](https://img.shields.io/badge/Version-2.20.4.1-yellowgreen)](#)
[![View - Documentation](https://img.shields.io/badge/View-Documentation-2ea44f)](https://docs.ycrash.io)
<!-- [![Artifact Hub](https://img.shields.io/endpoint?url=https://artifacthub.io/badge/repository/yCrash)](#https://artifacthub.io/packages/search?repo=ycrash) -->

## Usage

[Helm](https://helm.sh) must be installed to use the charts.
Please refer to Helm's [documentation](https://helm.sh/docs/) to get started.

Once Helm is set up properly, add the repo as follows:

<!-- ```console
helm repo add ycrash https://ycrash.github.io/helm-charts
``` -->

### Get Repo Info

```console
helm repo add ycrash https://ycrash.github.io/helm-charts
helm repo update ycrash
helm repo list
```

### Installing the Chart

To install the chart with the release name `ycrash`:

```console
helm install ycrash ycrash/ycrash
```
### Uninstalling the Chart

To uninstall the chart with the release name `ycrash`:

```console
helm uninstall ycrash --keep-history
```

To remove all the Kubernetes components associated with the chart and delete the release name `ycrash`:

```console
helm delete ycrash
```

### Search the Chart
```console
helm search repo ycrash --versions
```

## yCrash Server Helm Charts
Installs the Non-intrusive, AI aided, Instant root cause analysis tool [yCrash](http://ycrash.io/)

1. Download your `license.lic` file from [here](https://ycrash.io/yc-trial.jsp) or send an email to support@tier1app.com.

2. Run helm install / upgrade:

```console
helm upgrade -i ycrash ycrash/ycrash --set-file ycrash.secrets.license.content=license.lic
```

or with S3 storage:

```console
helm upgrade -i ycrash ycrash/ycrash \
  --set-file ycrash.secrets.license.content=license.lic \
  --set ycrash.storage.s3.endPointUrl=https://s3.us-west-1.amazonaws.com \
  --set ycrash.storage.s3.region=us-west-1 \
  --set ycrash.storage.s3.bucketName=my-bucket \
  --set ycrash.storage.s3.accessKey=my-access-key \
  --set ycrash.storage.s3.secretKey=my-secret-key
```

See [charts/ycrash/values.yaml](charts/ycrash/values.yaml) for the complete configuration values.


## BuggyApp Helm Charts

```console
helm upgrade -i buggyapp ycrash/buggyapp --set buggyapp.secrets.agentConfig.options.k=Licensee@UserNo
```

*Get your key (Licensee@UserNo) from your `license.lic` file.*

See [charts/buggyapp/values.yaml](charts/buggyapp/values.yaml) for the complete configuration values.

