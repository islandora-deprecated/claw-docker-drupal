# Islandora CLAW: Drupal Docker Image

[![Docker Stars](https://img.shields.io/docker/stars/islandora/claw-drupal.svg)](https://hub.docker.com/r/islandora/claw-drupal/)
[![Docker Pulls](https://img.shields.io/docker/pulls/islandora/claw-drupal.svg)](https://hub.docker.com/r/islandora/claw-drupal/)
[![Contribution Guidelines](http://img.shields.io/badge/CONTRIBUTING-Guidelines-blue.svg)](./CONTRIBUTING.md)
[![LICENSE](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](./LICENSE)

## Introduction

Defines the Drupal Docker image. 

Based on the [Base Docker Image](https://github.com/Islandora-CLAW/docker-base).

## Includes

* Drupal 7
* Apache 2
* PHP 5.6

## Build Arguments

| Variable       | Required | Default |
|----------------|----------|---------|
| DRUPAL_VERSION | no       |    7.43 |
| DRUSH_VERSION  | no       |   8.0.2 |

**Example:**
```bash
docker build --build-arg "DRUPAL_VERSION=7.41" -t islandora/claw-drupal .
```

## Environment Variables

| Variable                        | Required | Default                 |
|---------------------------------|----------|-------------------------|
| MYSQL_HOST                      | yes      | **see below**           |
| MYSQL_HOST_PORT                 | yes      | **see below**           |
| MYSQL_ROOT_USER                 | no       | root                    |
| MYSQL_ROOT_PASSWORD             | yes      |                         |
| DRUPAL_SITE_INSTALL_PROFILE     | no       | standard                |
| DRUPAL_SITE_NAME                | no       | Islandora CLAW          |
| DRUPAL_SITE_EMAIL               | no       | webmaster@localhost.com |
| DRUPAL_SITE_LOCALE              | no       | en-us                   |
| DRUPAL_SITE_ACCOUNT_NAME        | no       | admin                   |
| DRUPAL_SITE_ACCOUNT_PASSWORD    | yes      |                         |
| DRUPAL_SITE_ACCOUNT_EMAIL       | no       | webmaster@localhost.com |
| DRUPAL_SITE_DB_NAME             | no       | drupal_default          |
| DRUPAL_SITE_DB_USER             | no       | drupal                  |
| DRUPAL_SITE_DB_PASSWORD         | yes      |                         |
| DRUPAL_SITE_DB_REPLACE_EXISTING | no       | no                      |

Please consult the [parent image](https://github.com/Islandora-CLAW/docker-base).

**MYSQL_HOST & MYSQL_HOST_PORT:** If you link with the MariaDB container or equivalent these variables are not required as it's provided by the linked container.

**DRUPAL_SITE_DB_REPLACE:** If set to 'yes', the Drupal database will be replaced on start-up; useful for debugging, but not recommend for production sites.

**Example (foreground, random host port mapping, auto-remove, interactive shell):**
```bash
docker run --rm -ti -P  \
                    --link="mariadb:mysql" \
                    -e "MYSQL_ROOT_PASSWORD=your_super_secure_password" \
                    -e "DRUPAL_SITE_ACCOUNT_PASSWORD=your_super_secure_password" \
                    -e "DRUPAL_SITE_DB_PASSWORD=your_super_secure_password" \
                    islandora/claw-drupal ash
```

## Commands

For convenience a number of commands are provided in the [commands](/commands)
folder.

| Command | Arguments | Defaults | Notes                                       |
|---------|-----------|----------|---------------------------------------------|
| build   |           |          | Build this image with the default settings. |

## Notes

This is **not** a stand alone image it needs a database image or external database to connect to, you can either provide the required environment variables to a working database, or you can link this container with something equivalent. 

## Maintainers/Sponsors

* UPEI
* discoverygarden inc.
* LYRASIS
* McMaster University
* University of Limerick
* York University
* University of Manitoba
* Simon Fraser University
* PALS
* American Philosophical Society
* common media inc.

Current maintainers:

* [Nigel Banks](https://github.com/nigelgbanks)
* [Nick Ruest](https://github.com/ruebot)

## Development

If you would like to contribute, please get involved by attending our weekly [Tech Call](https://github.com/Islandora-CLAW/CLAW/wiki). We love to hear from you!

If you would like to contribute code to the project, you need to be covered by an Islandora Foundation [Contributor License Agreement](http://islandora.ca/sites/default/files/islandora_cla.pdf) or [Corporate Contributor Licencse Agreement](http://islandora.ca/sites/default/files/islandora_ccla.pdf). Please see the [Contributors](http://islandora.ca/resources/contributors) pages on Islandora.ca for more information.

## License

[MIT](https://opensource.org/licenses/MIT)
