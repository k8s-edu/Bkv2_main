
# Grafana stack


_This is a Helm chart, modified for educational purposes_ from [fluent-bit](https://github.com/fluent/helm-charts/tree/main/charts/fluent-bit), [loki](https://github.com/grafana/loki/tree/main/production/helm/loki), [tempo](https://github.com/grafana/helm-charts/tree/main/charts/tempo) [pyroscope](https://github.com/grafana/pyroscope/tree/main/operations/pyroscope/helm/pyroscope)


## Changed values from origin chart
| Chart | Field Path | Origin Value | Chanaged Value | Description |
| --- | --- | --- | --- | --- |
| loki | `loki.auth_enabled` | `true` | `false` | Simplify the experimental configuration by not performing additional user authentication. |
| loki | `loki.commonConfig.replication_factor` | `3` | `1` | Since the experimental configuration uses a single configuration mode, the log replica is set to 1. |
| loki | `loki.storage.type` | `s3` | `filesystem` | Since cloud storage cannot be used, it is set to use the local file system (disk). |
| loki | `loki.schemaConfig` | `{}` | `{"configs":[{"from":"2024-01-01T00:00:00Z","store":"tsdb","object_store":"filesystem","schema":"v13","index":{"prefix":"index_","period":"24h"}}]}` | Loki storage setting  |
| loki | `loki.test.enabled` | `true` | `false` | To proceed with the configuration without using additional resources, the test process is not performed. |
| loki | `loki.lokiCanary.enabled` | `true` | `false` | To proceed with the configuration without using additional resources, the canary test is not performed. |
| loki | `loki.listener.enableIPv6` | `true` | `false` | Since IPv6 is not provided in the experimental environment, this option is not used. |
| loki | `loki.singleBinary.replicas` | `0` | `1` | Since it is configured in single binary mode, the singleBinary.replica required for microservice deployment is set to 1. |
| loki | `loki.write.replicas` | `3` | `0` | Since it is configured in single binary mode, the write.replica required for microservice deployment is set to 0. |
| loki | `loki.read.replicas` | `3` | `0` | Since it is configured in single binary mode, the read.replica required for microservice deployment is set to 0. |
| loki | `loki.backend.replicas` | `3` | `0` | Since it is configured in single binary mode, the backend.replica required for microservice deployment is set to 0. |
| loki | `loki.resultsCache.enabled` | `true` | `false` | To avoid OOM (OutOfMemory), the query result cache is not used. This may cause delays in displaying search results. |
| loki | `loki.chunksCache.enabled` | `true` | `false` | To avoid OOM (OutOfMemory), the log content (chunk) cache is not used. This may cause delays in displaying search results. |
| fluent-bit | `fluent-bit.testFramework.enabled` | `true` | `false` | To proceed with the configuration without using additional resources, the test process is not performed. |
| tempo | `tempo.runAsNonRoot` | `true` | `false` | Tempo does not use root privileges. |
| pyroscope | `pyroscope.alloy.enabled` | `true` | `false` | To reduce resources and collect profile data, Pyroscope is configured standalone. Therefore, Alloy is not deployed together with Pyroscope. |
