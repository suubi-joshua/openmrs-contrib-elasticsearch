# openmrs-contrib-elasticsearch

Elasticsearch Docker image with `analysis-phonetic` plugin pre-installed for OpenMRS.

## Usage

Reference the custom image in your `values.yaml` or `kind-openmrs.yaml`.
The `image` field is set at the top level of the ECK Elasticsearch spec,
alongside `version`. **You must also remove any `initContainers` that install
`analysis-phonetic`** — the plugin is already baked into this image.

```yaml
elasticsearch-eck:
  version: "8.15.3"
  image: openmrs/openmrs-contrib-elasticsearch:8.15.3
  nodeSets:
    - name: default
      count: 1
      config:
        node.store.allow_mmap: false
      podTemplate:
        spec:
          # No initContainers needed — analysis-phonetic is pre-installed
          containers:
            - name: elasticsearch
              resources:
                requests:
                  memory: "2Gi"
                limits:
                  memory: "2Gi"
```

## Build locally

```sh
docker build --build-arg ES_VERSION=8.15.3 -t openmrs-contrib-elasticsearch:8.15.3 .
```

## Published images

Published to Docker Hub as `openmrs/openmrs-contrib-elasticsearch` via GitHub Actions on push to `main`.
