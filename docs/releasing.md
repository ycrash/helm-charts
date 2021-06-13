# Releasing New Chart Versions

We use [Chart Releaser](https://github.com/helm/chart-releaser) to release charts in this repo.


## Pre-requisites

1. Download chart-releaser to your bin path

2. Get a [GitHub personal access token](https://github.com/settings/tokens) with scope:
   - [x] repo

3. Setup env vars

   ```bash
   export CR_OWNER=ycrash
   export CR_GIT_REPO=helm-charts
   export CR_TOKEN="YOUR_TOKEN_FROM_STEP_2"
   ```

   For more configuration, see [https://github.com/helm/chart-releaser](https://github.com/helm/chart-releaser).

4. Bump chart versions, update the chart files and commit the changes:
  - [charts/ycrash/Chart.yaml](../charts/ycrash/Chart.yaml)
  - [charts/buggyapp/Chart.yaml](../charts/buggyapp/Chart.yaml)

5. Run cr package:

   ```bash
   cr package ./charts/ycrash
   ```

6. Run cr upload:

   ```bash
   cr upload --skip-existing
   ```

7. Run cr index:

   ```bash
   cr index --charts-repo=https://ycrash.github.io/helm-charts --push
   ```

   *Note: There is a known bug in cr v1.2.1. A quick workaround is to use v1.2.0 or upgrade to newer version*.
   *In v1.2.1, ssh remote is not supported to run cr index, so you would need to add a https remote:*

   ```
   git remote add origin-https https://github.com/ycrash/helm-charts.git
   cr index --charts-repo=https://ycrash.github.io/helm-charts --push --remote origin-https
   ```

