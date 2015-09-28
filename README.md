docker-data
===========

This repo contains a `Dockerfile` which helps to create minimalistic
Docker data container. The Docker image has 0 bytes:

```
$ docker images
REPOSITORY                   TAG                 IMAGE ID            CREATED             VIRTUAL SIZE
jtyr/data                    latest              1d8f511bd16b        6 seconds ago       0 B
```


Usage
-----

Pull the data image:

```
$ docker pull jtyr/data
```

Create a new data container with `/data` volume:

```
$ docker create -v /data --name my_data jtyr/data
```

Run application container (`my/app_container`) using the data container
(`my_data`) as a storage for the content of the `/data` directory:

```
$ docker run -d --volumes-from my_data --name my_container my/app_container
```

Pull data from the container:

```
$ docker cp my_data:/data ./
```


License
-------

MIT


Author
------

Jiri Tyr
