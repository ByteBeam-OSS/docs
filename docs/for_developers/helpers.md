# Helper Commands

To automate and simplify many everyday tasks, our team has created and maintains a variety of helpers under /bin in the SexyCoders main repository.

## sc-docker-build  

The docker build script builds docker images using the secycoders naming convention and automates versioning.

It also provides additionall options to change the name, push to the registry and include the "latest" tag when pushing for production.

We can see the available commands using the "--help" flag:

```bash
Usage: ./sc-docker-build [OPTIONS]

Options:
  -h, --help         Show this help message and exit
  -p, --push         Optionally push the image to the registry
  -l, --latest       Additionally tag the image as 'latest'
  -n, --name NAME    The name to be used for the Docker image (optional)
```

The name is determined in the following oder:

+ "--name" flag is provided
+ name is read from local "name" file
+ name is generated from current dir name

&#x26A0; In case a --name flag is provided but a name file already exists you will be prompted on whether to overwrite.

