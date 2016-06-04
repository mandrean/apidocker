# apiDocker

*apiDoc*ker is a minimalistic Alpine-based Docker image for generating API documentation from inline apidocjs.com annotation.

## Annotation
See apidocjs.com for full documentation with examples.

## Paths
You can specify _input_ and _output_ folder paths using the ENV variables:

*APIDOCKER_INPUT*

*APIDOCKER_OUTPUT*

Default paths are _/_ and _docs/_.

## Usage
With docker run, using the current working directory _$(pwd)_ and overriding the input/output paths:
```bash
docker run --rm -ti \
    -e APIDOCKER_INPUT="app/" \
    -e APIDOCKER_OUTPUT="apidocs/" \
    -v $(pwd):/src mandrean/apidocker
```
With docker-compose.yml, using the same working directory as the compose file and overriding the input/output paths:
```yaml
version: '2'

services:
    apidocker:
        image: mandrean/apidocker:latest
        environment:
            APIDOCKER_INPUT: app/
            APIDOCKER_OUTPUT: apidocs/
        volumes:
            - ./:/src
```

## TODO
- [ ] Add support for file-filters
- [ ] Add support for exclude filters
- [ ] Add support for templates
- [ ] Add support for apidoc config file
- [ ] Add support for verbose debug output
