# Schema Registry

## Gradle
Open and import as gradle project
```shell
gradle generateSchema
```

## Start the Schema Registry Server
```shell
docker-compose up -d
```
Waiting all ready

```shell
docker-compose down
```

## gitops
[schema-registry-gitops](https://github.com/domnikl/schema-registry-gitops/tree/main)
```shell
docker rm schema-registry-gitops
docker run --name schema-registry-gitops -v ./src/main/avdl:/avdl \
  domnikl/schema-registry-gitops:1.9.0 plan --registry http://host.docker.internal:8081 \
  /avdl/com/databius/schemabius/.state.yml
```

```shell
docker rm schema-registry-gitops
docker run --name schema-registry-gitops -v ./src/main/avdl:/avdl \
  domnikl/schema-registry-gitops:1.9.0 apply --registry http://host.docker.internal:8081 \
  /avdl/com/databius/schemabius/.state.yml
```