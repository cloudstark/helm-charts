## PostgREST

[PostgREST](https://postgrest.org/) is a standalone web server that turns your
PostgreSQL database directly into a RESTful API. The structural constraints and
permissions in the database determine the API endpoints and operations.

Using PostgREST is an alternative to manual CRUD programming. Custom API
servers suffer problems. Writing business logic often duplicates, ignores or
hobbles database structure. Object-relational mapping is a leaky abstraction
leading to slow imperative code. The PostgREST philosophy establishes a single
declarative source of truth: the data itself.

### Introduction

This chart deploys PostgREST to your cluster via a Deployment and Service. Optionally you can also enable ingress.

### Customization

The following options are supported. See [values.yaml](https://gitlab.smb-tec.com/charts/postgrest/blob/master/values.yaml)
for more detailed documentation and examples:

| Parameter 	                | Description 	                                              | Default               |
|---------                    |-----------	                                                |-------	              |
|`replicaCount`               | Number of replicas                                          | `1`	                  |
|`image.repository`           | The image to run	                                          | `postgrest/postgrest` |
|`image.tag`                  | The image tag to pull                                       | `v5.2.0`              |
|`image.pullPolicy`           |                                                             | `IfNotPresent`        |
|`nameOverride`               |                                                             | n/a                   |
|`fullnameOverride`           |                                                             | n/a                   |
|`service.type`               | Type of Service                                             | `ClusterIP`           |
|`service.port`               | Port for kubernetes service                                 | `80`        |
|`service.annotations`        | Annotations to add to the service                           | `{}`        |
|`ingress.enabled`            | If true, PostGREST Ingress will be created                  | `false`     |
|`ingress.annotations`        | PostGREST Ingress annotations                               | `{}`        |
|`ingress.hosts`              | PostGREST Ingress host names                                | `[]`        |
|`ingress.tls`                | PostGREST Ingress TLS configuration (YAML)                  | `[]`        |
|`resources`                  | CPU/Memory resource requests/limits                         | `{}`        |
|`nodeSelector`               | Settings for nodeselector                                   | `{}`        |
|`tolerations`                | Settings for toleration                                     | `[]`        |
|`affinity`                   | Settings for affinity                                       | `{}`        |
|`postgrest.db_uri`           | PostgreSQL connection                                       | n/a         |
|`postgrest.db_schema`        | Database schema to expose                                   | `public`    |
|`postgrest.db_anon_role`     | Database role to use                                        | n/a         |
|`postgrest.db_pool`          | Number of connections to keep open                          | `100`       |
|`postgrest.server_host`      | Where to bind the PostgREST web server                      | `*4`        |
|`postgrest.server_port`      | The port to bind the web server                             | `3000`      |
|`postgrest.server_proxy_uri` | Overrides the base URL                                      | n/a`        |
|`postgrest.jwt_secret`       | The secret or JSON Web Key (JWK) used to decode JWT tokens  | n/a         |
|`postgrest.secret_is_base64` |                                                             | `false`     |
|`postgrest.jwt_aud`          |                                                             | n/a         |
|`postgrest.max_rows`         | A hard limit to the number of rows PostgREST will fetch     | n/a         |
|`postgrest.pre_request`      | A schema-qualified stored procedure                         | n/a         |
|`postgrest.role_claim_key`   |                                                             | `.role`     |

> **Tip**: You can use the default [values.yaml](values.yaml)

> **Tip**: See [http://postgrest.org](http://postgrest.org/en/v4.3/install.html#configuration) for more detailed documentation