Base files for building the AppBuilder production api-sails Docker image.


# Preface
Intended to be used in a stack with MariaDB, redis, and others. For the official
stack, please see https://github.com/appdevdesigns/ab-production-stack/

The goal is to build a full working image deterministically from the standard
tools and repositories. There should be no ambiguity about the origin of any
component.


# Requirements
At build time the image will have root:root as the configured DB credentials.
The runtime DB password must be mounted in a plaintext file located
at "/secret/password". The included `ab-launcher.js` will update the config
files accordingly before each launch.

A custom `local.js` config file may be mounted into the "/app/config/"
directory to change various settings. However, "/secret/password" still
supercedes that for the DB password, unless you bypass `ab-launcher.js`.


# Example usage
`docker build --compress -t digiserve/ab-sails-api .`
