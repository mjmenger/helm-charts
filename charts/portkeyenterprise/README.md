## Usage

[Helm](https://helm.sh) must be installed to use the charts.  Please refer to
Helm's [documentation](https://helm.sh/docs) to get started.

Once Helm has been set up correctly, add the repo as follows:

  `helm repo add mjmenger https://mjmenger.github.io/helm-charts`

If you had already added this repo earlier, run `helm repo update` to retrieve the latest versions of the packages.  You can then run `helm search repo mjmenger` to see the charts.

To install the portkeyenterprise chart:

    helm install my-releasename mjmenger/portkeyenterprise

To uninstall the chart:

    helm delete my-releasename

## Create a file with configuration parameters
In this example, it is saved as `environment.yaml`
```yaml
environment:
  create: true
  secret: true
  data:
    CLICKHOUSE_FEEDBACK_TABLE: abc
    CLICKHOUSE_HOST: https://clickhouseurl:8443
    CLICKHOUSE_KV_HASH_MAP_TABLE: abc
    CLICKHOUSE_LOG_TABLE: abc
    CLICKHOUSE_PASSWORD: abc
    CLICKHOUSE_USER: abc
    MONGO_COLLECTION_NAME: abc
    MONGO_DATABASE: abc
    MONGO_DB_CONNECTION_URL: abc
    PORTKEY_API_KEY: abc
    PORTKEY_ORGANISATION_ID: abc
    REDIS_TLS_ENABLED: "abc"
    REDIS_URL: redis://redis:6379
    SERVICE_NAME: abc
```
you can find the latest version of the environment inputs by using `helm show values mjmenger/portkeyenterprise`

## Create dry-run manifest
change the name `example` as appropriate for your release
```shell
helm install -n portkeyenterprise --dry-run=client example mjmenger/portkeyenterprise -f ./environment.yaml
```

## Apply helm chart
change the name `example` as appropriate for your release
```shell
helm install -n portkeyenterprise example mjmenger/portkeyenterprise -f ./environment.yaml
```    