MemSQL Official Docker Image
============================

The official docker image for testing MemSQL + MemSQL Ops (cluster-in-a-box).

Check out the tutorial:
http://docs.memsql.com/docs/quick-start-with-docker/

### Example usage

```
# Pull the image
docker pull memsql/quickstart


# Verify your machine satisfies our minimum requirements
docker run --rm memsql/quickstart check-system


# Spin up a MemSQL cluster on your machine
docker run -d -p 3306:3306 -p 9000:9000 --name=memsql memsql/quickstart


# Run a quick benchmark against MemSQL
docker run --rm -it --link=memsql:memsql memsql/quickstart simple-benchmark


# Open a MemSQL command line shell
docker run --rm -it --link=memsql:memsql memsql/quickstart memsql-shell


# Stop and remove the container
docker rm -fv memsql
```

### Custom schema file at start

If you mount a SQL file to /schema.sql inside the container it will be loaded
when the cluster is started. Example:

```
echo "CREATE DATABASE test;" > schema.sql
docker run -d -v $(PWD)/schema.sql:/schema.sql -p 3306:3306 -p 9000:9000 --name=memsql memsql/quickstart
```
