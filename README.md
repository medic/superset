# Readme

[Apache Superset](https://superset.apache.org/) Docker image with additional libraries used with Medic's CHT deployments. This follows Superset's [advice about using a custom image](https://superset.apache.org/docs/installation/docker-builds/#building-your-own-production-docker-image).

# Docker Image
This docker image currently comes with following packages installed that are used in generally most of the superset deployments Medic is supporting. 

- [psycopg2-binary](https://pypi.org/project/psycopg2-binary/): To connect to postgres databases
- [Authlib](https://docs.authlib.org/en/latest/): To support OAuth login
- [openpyxl](https://pypi.org/project/openpyxl/): To support uploading excel files for analysis
- [Pillow](https://pypi.org/project/pillow/): For Alert and Report
- [playwright](https://pypi.org/project/playwright/): For taking screenshots for Alerts & Reports

## Usage
To use this version of superset on your deployments, update your Helm `values.yaml` to point to this superset image repo instead of `apachesuperset.docker.scarf.sh/apache/superset`

```yaml
image:
  repository: public.ecr.aws/medic/superset
  tag: "6.1.0"
  pullPolicy: IfNotPresent
```

We keep image tags in sync with the upstream Apache Superset image. Each tag below maps to the matching `apache/superset` version.

Images published from this repo are multi-architecture manifests covering `linux/amd64` and
`linux/arm64`, so a single tag works on x86_64 hosts and on arm64 hosts such as AWS Graviton.
Docker and Kubernetes pick the matching architecture automatically — no change to `values.yaml`
is needed. Older tags built before arm64 support was added remain `amd64`-only; see the table below.

## Available Images
The following tags are published to [`public.ecr.aws/medic/superset`](https://gallery.ecr.aws/medic/superset):

| Tag | Apache Superset version | Architectures |
| --- | --- | --- |
| `latest` | Points to the most recently published version below | `amd64`, `arm64` |
| `6.1.0` | 6.1.0 | `amd64`, `arm64` |
| `5.0.0` | 5.0.0 | `amd64` |
