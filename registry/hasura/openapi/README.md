# OpenAPI Lambda Connector

[![Docs](https://img.shields.io/badge/docs-v3.x-brightgreen.svg?style=flat)](https://hasura.io/docs/3.0)
[![ndc-hub](https://img.shields.io/badge/ndc--hub-openapi-blue.svg?style=flat)](https://hasura.io/connectors/open-api-lambda)
[![License](https://img.shields.io/badge/license-Apache--2.0-purple.svg?style=flat)](https://www.apache.org/licenses/LICENSE-2.0)

The OpenAPI Lambda Connector allows you to import APIs that are documented in the OpenAPI/Swagger format into the Hasura Supergraph. The connector exposes REST API endpoints as Typescript functions, which can be exposed as GraphQL queries or mutations via the [NodeJS Lambda Connector](https://github.com/hasura/ndc-nodejs-lambda).

Functions that wrap GET requests are marked with a `@readonly` annotation, and are exposed as GraphQL Queries by the [NodeJS Lambda Connector](https://github.com/hasura/ndc-nodejs-lambda). All other request types are exposed as GraphQL Mutations.

This Connector implements the [Data Connector Spec](https://github.com/hasura/ndc-spec)

- [See the listing in the Hasura Hub](https://hasura.io/connectors/open-api-lambda)
- [Hasura DDN Documentation](https://hasura.io/docs/3.0)
- [Hasura DDN Quickstart](https://hasura.io/docs/3.0/getting-started/quickstart)
- [NodeJS Lambda Connector](https://github.com/hasura/ndc-nodejs-lambda)

Docs for the OpenAPI data connector:

- [Documentation](https://github.com/hasura/ndc-open-api-lambda/blob/main/docs/documentation.md)
- [Contributing](https://github.com/hasura/ndc-open-api-lambda/blob/main/docs/contributing.md)
- [Code of Conduct](https://github.com/hasura/ndc-open-api-lambda/blob/main/docs/code-of-conduct.md)
- [Relase Document](https://github.com/hasura/ndc-open-api-lambda/blob/main/docs/release.md)

## Features

- Convert Open API/swagger documentation into Typescript functions compatible with NodeJS Lambda Connector
- Supported request types

| Request Type | Query | Path | Body | Headers |
| ------------ | ----- | ---- | ---- | ------- |
| GET          | ✅    | ✅   | NA   | ✅      |
| POST         | ✅    | ✅   | ✅   | ✅      |
| DELETE       | ✅    | ✅   | ✅   | ✅      |
| PUT          | ✅    | ✅   | ✅   | ✅      |
| PATCH        | ✅    | ✅   | ✅   | ✅      |

## Before you get Started

1. Create a [Hasura Cloud account](https://console.hasura.io)
2. Please ensure you have the [DDN CLI](https://hasura.io/docs/3.0/cli/installation) and [Docker](https://docs.docker.com/engine/install/) installed
3. [Create a supergraph](https://hasura.io/docs/3.0/getting-started/init-supergraph)
4. [Create a subgraph](https://hasura.io/docs/3.0/getting-started/init-subgraph)
5. If you want to make changes to the generated Typescript files, please ensure you have Node.js v20+ installed

## Using the OpenAPI connector

### Step 1: Authenticate your CLI session

```bash
ddn auth login
```

### Step 2: Configure the connector

Once you have an initialized supergraph and subgraph, run the initialization command in interactive mode while
providing a name for the connector in the prompt:

```bash
ddn connector init <connector-name> -i
```

#### Step 2.1: Choose `hasura/openapi` from the list

#### Step 2.2: Choose a port for the connector

The CLI will ask for a specific port to run the connector on. Choose a port that is not already in use or use the
default suggested port.

#### Step 2.3: Provide the env vars required for the connector

Environment variables that can be used to configure the connector are listed under [Supported Environment Variables](https://github.com/hasura/ndc-open-api-lambda/blob/main/docs/documentation.md#supported-environment-variables).

## Step 3: Introspect the connector

```bash
ddn connector introspect <connector-name>
```

This will generate the required metadata and TypeScript files.

## Step 4: Add your resources

```bash
ddn connector-link add-resources <connector-name>
```

This command will track all the API endpoints in your OpenAPI Document as [Commands](https://hasura.io/docs/3.0/supergraph-modeling/commands/).

## Saving User Changes

Please refer to [Saving User Changes](https://github.com/hasura/ndc-open-api-lambda/blob/main/docs/documentation.md#saving-user-changes).

## Known Limiations

- Support for [Relaxed Types](https://github.com/hasura/ndc-nodejs-lambda/tree/main?tab=readme-ov-file#relaxed-types) is a WiP.
- [Types not supported by the NodeJS Lambda Connector](https://github.com/hasura/ndc-nodejs-lambda?tab=readme-ov-file#unsupported-types) are not supported.

## Contributing

Check out our [contributing guide](.docs/contributing.md) for more details.

## Changelog

Please refer to the [changelog](https://github.com/hasura/ndc-open-api-lambda/blob/main/changelog.md).

## License

The Open API Lambda Connector is available under the [Apache License 2.0](https://www.apache.org/licenses/LICENSE-2.0).
