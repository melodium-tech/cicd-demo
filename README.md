# CI/CD Mélodium Demo

This is demonstration code for basic CI/CD.

## Execute

Install `melodium` command: https://melodium.tech/en/download

`melodium run --api-report ./Compo.toml advanced --repository_clone_url "$CI_REPOSITORY_URL" --repository_clone_ref "$CI_COMMIT_REF_NAME"`

Main [entrypoint](https://doc.melodium.tech/book/en/programming/project_organization/entrypoints.html#entrypoints-parameters) is can be launched with more parameters

## Github

The Github job token is granted the right to write statuses in order to report them.

## GitLab

It is required to fill a variable `GITLAB_PAT` with personnal access token in order to report states through the GitLab API.

## Cadence.CI

`MELODIUM_API_TOKEN` is for Cadence.CI information reporting and API exchange in case of remote execution: https://cadence.ci/en/dashboard/tokens

`--build_location` and `--test_location` can either be `compose` (which makes use of local container Docker/Podman Compose command), or `api` (which pass through Cadence.CI API to connect to execution cluster): https://doc.melodium.tech/latest/en/cicd/runners/CicdDispatchEngine.html  
In both cases, the api will get reports of the execution if the `MELODIUM_API_TOKEN` is valid.
