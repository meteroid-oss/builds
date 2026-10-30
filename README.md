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

This repository hosts the [Meteroid](https://github.com/meteroid-oss/meteroid) official Docker images.

## Docker Images

Pre-built images are available on GitHub Container Registry:

```bash
docker pull ghcr.io/meteroid-oss/meteroid-api:latest
docker pull ghcr.io/meteroid-oss/meteroid-scheduler:latest
docker pull ghcr.io/meteroid-oss/metering-api:latest
docker pull ghcr.io/meteroid-oss/meteroid-web:latest
```

Images are built for both `linux/amd64` and `linux/arm64` platforms.

## Image Security

- **Signed**: every published image is signed with [Sigstore cosign](https://docs.sigstore.dev/) (keyless, GitHub OIDC) and carries a CycloneDX SBOM attestation.
- **Scanned**: every build is scanned with [Trivy](https://trivy.dev/) before it is tagged; fixable critical vulnerabilities block the release.
- **Fresh**: OS packages are upgraded on every build, and the latest release is rebuilt weekly on the latest base images.
  Exact version tags (`1.2.3`) never change; the rebuild moves the floating tags (`1.2`, `1`, `latest`) and is also tagged `v1.2.3-YYYYMMDD`.

Verify a signature:

```bash
cosign verify ghcr.io/meteroid-oss/meteroid-api:latest \
  --certificate-identity https://github.com/meteroid-oss/builds/.github/workflows/docker.yaml@refs/heads/main \
  --certificate-oidc-issuer https://token.actions.githubusercontent.com
```

Fetch the SBOM:

```bash
cosign verify-attestation --type cyclonedx ghcr.io/meteroid-oss/meteroid-api:latest \
  --certificate-identity https://github.com/meteroid-oss/builds/.github/workflows/docker.yaml@refs/heads/main \
  --certificate-oidc-issuer https://token.actions.githubusercontent.com \
  | jq -r .payload | base64 -d | jq .predicate
```

## License

These images are the official Meteroid distribution: the open-source core plus enterprise modules, under the Meteroid license.
They run free without a license key; a license key unlocks enterprise features in place.

- **Contact us**: [meteroid.com/book-a-demo](https://meteroid.com/book-a-demo)
- **Email**: contact@meteroid.com

### Looking for the Open Source Version?

The [Meteroid repository](https://github.com/meteroid-oss/meteroid) stays AGPL-licensed; you can build it yourself from its Dockerfiles.
The `1.0.0-rc.*` images are no longer maintained; see the upgrade guide to move to 2.0.

## About Meteroid

Meteroid is a cloud-native pricing and billing infrastructure for product-led SaaS. It handles usage-based billing, subscription management, and revenue operations at scale.

[Learn more](https://www.meteroid.com?utm_source=github) | [Documentation](https://docs.meteroid.com)
