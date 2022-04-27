# [Wiremock](http://wiremock.org/) Starter

A simple example of how to stand-up one or more Wiremock servers on a development machine, using docker-compose, requiring only configuration files to be specified.

## Getting started

1. Run the `init` script to download pre-requisites

```shell
chmod u=rwx ./init.sh && ./init.sh
```

2. Start up the servers

```shell
docker-compose up -d
```

3. Test the endpoints

(`jq` is optionally used to pretty-print the response; omit if you don't like it.)
```shell
curl -s http://localhost:8090  | jq

curl -s http://localhost:8091  | jq

curl -s http://localhost:8090/ex1  | jq
```

4. Stop the servers

```shell
docker-compose down
```

## Usage

```shell
# start all servers in the background
docker-compose up -d

# restart all servers to honour any config changes
docker-compose restart

# delete all servers
docker-compose down
```

```shell
# or start all servers in the foreground
docker-compose up

# ctrl-c to stop
```

```shell
# start only one of the servers
docker-compose up server-a
```

## Notes

### Response Templating
To support [response templating](http://wiremock.org/docs/response-templating/), an extension must be downloaded first. This is then bind-mounted into the container, and enabled via the command options.

See the `docker-compose` configuration for `server-a` for an example.

The [./init.sh](./init.sh) script provided will download the required extension.

### Logging Verbosity
Verbose logging can be enabled by passing in the `--verbose` parameter to the Wiremock server via the `command` option to docker. 

See the `docker-compose` configuration for `server-a` for an example.

Any other command line parameters for Wiremock, detailed in the [documentaiton](http://wiremock.org/docs/running-standalone/#command-line-options) can be added in the same way.

## Resources

- See the [official documentation](http://wiremock.org/docs/request-matching/) for more information on configuring endpoints.

- See the [bx-dev-mocks](https://bitbucket.bics-collaboration.homeoffice.gov.uk/projects/BX/repos/bx-dev-tools/browse/bxdevmocks) for further configuration examples.

