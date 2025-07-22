<div align="center">

# typo3-docker

[![CGL](https://img.shields.io/github/actions/workflow/status/move-elevator/typo3-docker/build-and-publish-deployment.yaml?label=build&logo=github)](https://github.com/move-elevator/typo3-docker/actions/workflows/build-and-publish-deployment.yaml)
[![License](https://img.shields.io/github/license/move-elevator/typo3-docker)](LICENSE)

</div>

This repository provides docker images in [move:elevator](https://www.move-elevator.de/) TYPO3 projects. It is not meant to be used anywhere else.

- [PHP 8.4 with Composer](php8.4-composer/Dockerfile)

## ⚡ Usage

Use the desired image in your `docker-compose.yml` file or `.gitlab-ci.yml` file:

```yaml
image: ghcr.io/move-elevator/php8.4-composer:latest
```

## ⭐ License

This project is licensed under [GNU General Public License 3.0 (or later)](LICENSE).