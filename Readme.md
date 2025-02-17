# WrapDrive

[![Docker Image Build](https://github.com/brickdoc/wrapDrive/actions/workflows/build_image.yaml/badge.svg)](https://github.com/brickdoc/wrapDrive/actions/workflows/build_image.yaml)

Tiny Http static file server.

## Devolopment

```bash
make lint
make build
```

## Usage

```Dockerfile
# build static website
FROM node:16  as build
WORKDIR /app
ADD . /app
RUn yarn install && yarn build

# copy it into wrapdrive container
FROM ghcr.io/brickdoc/wrapdrive:latest
COPY --from=build /app/dist /var/www
CMD ["/wrapdrive"]
```

## License

Copyight (c) 2021 Brickdoc (Ningbo) Cloud Computing Technology LTD

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

[http://www.apache.org/licenses/LICENSE-2.0](http://www.apache.org/licenses/LICENSE-2.0)

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
