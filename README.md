# @immowelt/docker-publish

[![Greenkeeper badge](https://badges.greenkeeper.io/ImmoweltGroup/docker-publish.svg)](https://greenkeeper.io/)

[![Powered by Immowelt](https://img.shields.io/badge/powered%20by-immowelt-yellow.svg?colorB=ffb200)](https://stackshare.io/immowelt-group/)
[![Build Status](https://travis-ci.org/ImmoweltGroup/docker-publish.svg?branch=master)](https://travis-ci.org/ImmoweltGroup/docker-publish)

> A simple CLI to build and publish a repository with an Dockerfile based on GitHub repository release tags.

## Installing
```sh
npm i -D @immowelt/docker-publish
```

## Usage and examples
```
  Usage: DEBUG=@immowelt* docker-publish [options]

  Options:

    --github-api-tags-url <url>
    --versionBuildArgKey <string>
    --dockerImage <string>
```

#### Example usage
```sh
DEBUG=@immowelt* docker-publish --github-api-tags-url=https://api.github.com/repos/nodejs/node/tags --dockerImage=immowelt/node --versionBuildArgKey=NODE_VERSION
```

This command would build and push a docker image with the `Dockerfile` located in the processes `cwd` for each valid semver release tag of the official NodeJS repository. During the build we forward an `--build-arg`, e.g. `NODE_VERSION` with the current iterated version. After the build is done the image gets tagged e.g. `immowelt/node:8.3.0`.

After the iteration of releases is done, we also re-tag the `latest` tag of docker to make sure that the `latest` tag does in fact point to the last released version.

## Contributing
Please make sure that you adhere to our code style, you can validate your changes / PR by executing `npm run lint`.
Visit the [eslint-config-immowelt-react](https://github.com/ImmoweltHH/eslint-config-immowelt-react) package for more information.

## Licensing
See the LICENSE file at the root of the repository.
