# openmrs-contrib-elasticsearch

Elasticsearch Docker image with `analysis-phonetic` plugin pre-installed for OpenMRS.

## Usage

```yaml
elasticsearch-eck:
  version: "8.15.3"
  image: ghcr.io/openmrs/openmrs-contrib-elasticsearch:8.15.3
```

## Build locally

```sh
docker build --build-arg ES_VERSION=8.15.3 -t openmrs-contrib-elasticsearch:8.15.3 .
```

## Published images

Published to `ghcr.io/openmrs/openmrs-contrib-elasticsearch` via GitHub Actions on push to `main`.
