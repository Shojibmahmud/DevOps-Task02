## Docker Cloud application

This is example application which uses GitLab CI to test, build and deploy to Docker Cloud.

This example is configured, to:
1. run tests,
2. build docker image and store it in GitLab Container Registry,
3. deploy images, by:
  1. tagging them with `:staging` or `:production`,
  2. redeploying Docker Cloud service.

### Access environments

* Production: https://docker-cloud.gitlap.com/
* Staging: https://staging.docker-cloud.gitlap.com/

### Fork and configure

1. Fork this project,
1. Login to Docker Cloud,
1. Go to API Keys: https://cloud.docker.com/_/account,
1. Generate API key,
1. Put `DOCKERCLOUD_USER` and `DOCKERCLOUD_APIKEY` as Secure Variables.
1. Update service name of `staging` and `production` jobs of `.gitlab-ci.yml`.

### Example Stackfile on DockerCloud

This is currently used example stack file for `deployment-demo`:
```
production:
  image: 'registry.gitlab.com/gitlab-examples/docker-cloud:production'
  environment:
    - ENABLE_HTTP=true
    - VIRTUAL_HOST=production.162.243.115.26.xip.io

staging:
  image: 'registry.gitlab.com/gitlab-examples/docker-cloud:staging'
  environment:
    - ENABLE_HTTP=true
    - VIRTUAL_HOST=staging.162.243.115.26.xip.io
```
