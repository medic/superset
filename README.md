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
  tag: "5.0.0"
  pullPolicy: IfNotPresent
```

We'll keep image tags in sync with apache superset image and this repository currently supports Apache superset `5.0.0` and onwards. 