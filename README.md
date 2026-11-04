<div align="center">
  <a href="https://www.meteroid.com?utm_source=github" target="_blank">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://raw.githubusercontent.com/meteroid-oss/meteroid/main/assets/meteroid-logo-wordmark--dark.svg">
    <img alt="Meteroid Logo" src="https://raw.githubusercontent.com/meteroid-oss/meteroid/main/assets/meteroid-logo-wordmark--light.svg" width="280"/>
  </picture>
  </a>
</div>

<h3 align="center">Meteroid Builds</h3>

<p align="center">
  <a href="https://go.meteroid.com/discord?utm_source=github">
    <img src="https://img.shields.io/discord/1202199422910595155?logo=Discord&logoColor=%23FFFFFF&style=plastic" alt="Discord">
  </a>
  <a href="https://twitter.com/meteroidhq">
    <img alt="Twitter" src="https://img.shields.io/twitter/url.svg?label=meteroidhq&style=social&url=https%3A%2F%2Ftwitter.com%2Fmeteroidhq" />
  </a>
</p>

---

This repository builds the official [Meteroid](https://github.com/meteroid-oss/meteroid) Docker images and Helm chart.

## Docker Images

The images are the Meteroid distribution: the open-source core plus the Enterprise modules. They run free
without a license; a license unlocks the paid features. They are published on GitHub Container Registry,
for `linux/amd64` and `linux/arm64`, from 2.0 under these names:

```bash
docker pull ghcr.io/meteroid-oss/meteroid-api:latest
docker pull ghcr.io/meteroid-oss/meteroid-worker:latest
docker pull ghcr.io/meteroid-oss/metering-api:latest
docker pull ghcr.io/meteroid-oss/meteroid-web:latest
```

Tags: the release (`v2.0.0`, `2.0.0`, `2.0`, `2`, `latest`), `sha-<commit>` for every build of `main`, and `tip`
for the latest one. The former names (`meteroid-api-ee`, `meteroid-scheduler-ee`, `metering-api-ee`,
`meteroid-web-ee`) are published too until 2.0, and stop after it. Before 2.0 the plain names held the
open-source images up to `1.0.0-rc7`; see the [upgrade guide](https://docs.meteroid.com/self-hosting/upgrading-to-2-0).
The worker is also published as `meteroid-scheduler`, the name the old compose file and chart pull, so
an install that pulls `latest` moves all its images together.

The [Meteroid repository](https://github.com/meteroid-oss/meteroid) is AGPL-3.0 licensed; build the open-source
edition yourself from its Dockerfiles with `EDITION=oss`.

## Helm Chart

Each release also publishes a Helm chart pinned to that release's images:

```bash
helm install meteroid oci://ghcr.io/meteroid-oss/charts/meteroid --version 2.0.0 -f values.yaml
```

## Licenses

- **Contact us**: [meteroid.com/book-a-demo](https://meteroid.com/book-a-demo)
- **Email**: hey@meteroid.com

## About Meteroid

Meteroid is a cloud-native pricing and billing infrastructure for product-led SaaS. It handles usage-based billing, subscription management, and revenue operations at scale.

[Learn more](https://www.meteroid.com?utm_source=github) | [Documentation](https://docs.meteroid.com)
