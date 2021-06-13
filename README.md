# yCrash Helm Charts

## How to use yCrash Helm repository

```
helm repo add ycrash https://ycrash.github.io/helm-charts
helm repo update
```

## Helm Charts

### yCrash

1. Download your `license.lic` from [https://ycrash.io/](https://ycrash.io/).

2. Run helm install / upgrade:

```
helm upgrade -i ycrash ycrash/ycrash --set-file ycrash.secrets.license.content=license.lic
```

or with S3 storage:

```
helm upgrade -i ycrash ycrash/ycrash \
  --set-file ycrash.secrets.license.content=license.lic \
  --set ycrash.storage.s3.endPointUrl=https://s3.us-west-1.amazonaws.com \
  --set ycrash.storage.s3.region=us-west-1 \
  --set ycrash.storage.s3.bucketName=my-bucket \
  --set ycrash.storage.s3.accessKey=my-access-key \
  --set ycrash.storage.s3.secretKey=my-secret-key
```

See [charts/ycrash/values.yaml](charts/ycrash/values.yaml) for the complete configuration values.


### BuggyApp

```
helm upgrade -i buggyapp ycrash/buggyapp --set buggyapp.secrets.agentConfig.key=Licensee@UserNo
```

*Get your key (Licensee@UserNo) from your `license.lic` file.*

See [charts/buggyapp/values.yaml](charts/buggyapp/values.yaml) for the complete configuration values.

