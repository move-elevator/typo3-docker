<div align="center">

# typo3-docker

[![CGL](https://img.shields.io/github/actions/workflow/status/move-elevator/typo3-docker/build-and-publish-deployment.yaml?label=build&logo=github)](https://github.com/move-elevator/typo3-docker/actions/workflows/build-and-publish-deployment.yaml)
[![License](https://img.shields.io/github/license/move-elevator/typo3-docker)](LICENSE)

</div>

This repository provides docker images in [move:elevator](https://www.move-elevator.de/) TYPO3 projects. It is not meant to be used anywhere else.

- [PHP 8.4 with Composer](php8.4-composer/Dockerfile)
- [PHP 8.4 with Composer (slim)](php8.4-composer-slim/Dockerfile)
- [PHP 8.5 with Composer](php8.5-composer/Dockerfile)
- [PHP 8.5 with Composer (slim)](php8.5-composer-slim/Dockerfile)
- [PHP 8.5 with Composer and Node 24](php8.5-composer-node24/Dockerfile)
- [PHP 8.5 with Composer and Node 24 (slim)](php8.5-composer-node24-slim/Dockerfile)

The `slim` variants omit `python3-pip` and the legacy `db-sync-tool`/`file-sync-tool` Python packages. Use them once your project has migrated to [`konradmichalik/php-sync-tool`](https://github.com/konradmichalik/php-sync-tool).

## ⚡ Usage

Use the desired image in your `docker-compose.yml` file or `.gitlab-ci.yml` file:

```yaml
image: ghcr.io/move-elevator/php8.4-composer:latest
```

## ⭐ License

This project is licensed under [GNU General Public License 3.0 (or later)](LICENSE).