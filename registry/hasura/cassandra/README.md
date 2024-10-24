# Cassandra Connector

[![Docs](https://img.shields.io/badge/docs-v3.x-brightgreen.svg?style=flat)](https://hasura.io/docs/3.0/getting-started/overview/)
[![ndc-hub](https://img.shields.io/badge/ndc--hub-cassandra-blue.svg?style=flat)](https://hasura.io/connectors/cassandra)
[![License](https://img.shields.io/badge/license-Apache--2.0-purple.svg?style=flat)](LICENSE.txt)
[![Status](https://img.shields.io/badge/status-alpha-yellow.svg?style=flat)](./readme.md)

With this connector, Hasura allows you to instantly create a real-time GraphQL API on top of your data models in Cassandra.
This connector supports Cassandra's functionalities listed in the table below, allowing for efficient and scalable data
operations. Additionally, users benefit from all the powerful features of Hasura’s Data Delivery Network (DDN) platform,
including query pushdown capabilities that delegate query operations to the database, thereby enhancing query
optimization and performance.

This connector implements the [Data Connector Spec](https://github.com/hasura/ndc-spec).

- [Connector information in the Hasura Hub](https://hasura.io/connectors/cassandra)
- [Hasura V3 Documentation](https://hasura.io/docs/3.0)

## Features

Below, you'll find a matrix of all supported features for the Cassandra connector:

| Feature                         | Supported | Notes |
| ------------------------------- | --------- | ----- |
| Native Queries + Logical Models | ❌        |       |
| Native Mutations                | ❌        |       |
| Simple Object Query             | ✅        |       |
| Filter / Search                 | ✅        |       |
| Simple Aggregation              | ✅        |       |
| Sort                            | ✅        |       |
| Paginate                        | ✅        |       |
| Table Relationships             | ✅        |       |
| Views                           | ✅        |       |
| Remote Relationships            | ✅        |       |
| Custom Fields                   | ❌        |       |
| Mutations                       | ❌        |       |
| Distinct                        | ❌        |       |
| Enums                           | ❌        |       |
| Naming Conventions              | ❌        |       |
| Default Values                  | ❌        |       |
| User-defined Functions          | ❌        |       |

## Prerequisites

1. Create a [Hasura Cloud account](https://console.hasura.io)
2. Please ensure you have the [DDN CLI](https://hasura.io/docs/3.0/cli/installation) and
   [Docker](https://docs.docker.com/engine/install/) installed
3. [Create a supergraph](https://hasura.io/docs/3.0/getting-started/init-supergraph)
4. [Create a subgraph](https://hasura.io/docs/3.0/getting-started/init-subgraph)

## Using the Cassandra connector

With the [context set](https://hasura.io/docs/3.0/cli/commands/ddn_context_set/) for an existing subgraph, initialize
the connector:

```sh
ddn connector init -i
```

When the wizard runs, you'll be prompted to enter the following env vars necessary for your connector to function:

| Name                  | Description                          | Required |
| --------------------- | ------------------------------------ | -------- |
| CASSANDRA_HOST        | Cassandra Host                       | true     |
| CASSANDRA_KEYSPACE    | Cassandra KeySpace                   | true     |
| CASSANDRA_USERNAME    | Cassandra username                   | true     |
| CASSANDRA_PASSWORD    | Cassandra password                   | true     |
| CASSANDRA_PORT        | Cassandra port                       | false    |
| CASSANDRA_DC          | Cassandra Data Center                | false    |
| CASSANDRA_SSL_CA_PATH | Cassandra self-signed root cert path | false    |
| CASSANDRA_SSL         | Cassandra SSL                        | false    |

After the CLI initializes the connector, you'll need to:

- [Introspect](https://hasura.io/docs/3.0/cli/commands/ddn_connector_introspect) the source.
- Add your [models](https://hasura.io/docs/3.0/cli/commands/ddn_model_add),
  [commands](https://hasura.io/docs/3.0/cli/commands/ddn_command_add), and
  [relationships](https://hasura.io/docs/3.0/cli/commands/ddn_relationship_add).
- Create a [new build](https://hasura.io/docs/3.0/cli/commands/ddn_supergraph_build_local).
- Test it by [running your project along with the connector](https://hasura.io/docs/3.0/cli/commands/ddn_run#examples).

## License

The Hasura Cassandra connector is available under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).