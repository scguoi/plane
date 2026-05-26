# Publishing ForgeFlow Plane images to GHCR

The fork publishes Plane Community Edition component images to GitHub Container Registry with the
`publish-ghcr` workflow.

## Image names

The workflow publishes these images:

```text
ghcr.io/scguoi/plane-frontend:<tag>
ghcr.io/scguoi/plane-backend:<tag>
ghcr.io/scguoi/plane-admin:<tag>
ghcr.io/scguoi/plane-space:<tag>
ghcr.io/scguoi/plane-live:<tag>
ghcr.io/scguoi/plane-proxy:<tag>
```

For the default branch, the workflow also publishes `latest` for every image. Branch builds publish
a branch tag such as `preview`, and all builds publish a `sha-<commit>` tag.

## When images are published

Images are published when:

- commits are pushed to `preview` or `main`;
- tags matching `v*` are pushed;
- the workflow is started manually from GitHub Actions.

Documentation-only changes are ignored.

## Required GitHub settings

The workflow uses the repository `GITHUB_TOKEN` and requires:

- Actions enabled for the repository;
- workflow permissions allowing package writes;
- package visibility configured as needed after the first publish.

No Docker Hub credentials are required.

## Deployment note

The workflow builds the six core Plane component images for `linux/amd64` and `linux/arm64`.
The all-in-one community image should be added after the component image flow is stable.
