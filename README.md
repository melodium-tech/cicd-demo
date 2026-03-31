# CI/CD Mélodium Demo

This is demonstration code for basic CI/CD.

## Try it yourself

1. Fork the repository
2. Go on [Cadence.CI](https://cadence.ci), on  _Dashboard_ > _Execution_ > _Tokens_
3. Create a new _Run Token_
4. Depending on your platform:
    - On **Github**:
        1. _Settings_ > _Secrets and variables_ > _Actions_ > _Repository secrets_, add secret named `MELODIUM_API_TOKEN` and paste your token value as secret.
        2. Go on _Actions_, activate workflows.
        3. On `melodium-ci` action, trigger `Run worflow`
    - On **GitLab**:
        1. _Settings_ > _CI/CD_ > _Variables_ > _Add variable_, mark as masked and protected variable, with key `MELODIUM_API_TOKEN` and token as secret.
        2. Go on _Build_ > _Pipelines_, click _New pipeline_ then _New pipeline_ on the new page again.
5. On Cadence.CI dashboard, new execution runs should appear in _Execution_ > _Runs_.

## Specific informations

### Github

The Github job token is granted the right to write statuses in order to report them.

### GitLab

It is required to fill a variable `GITLAB_PAT` with personnal access token in order to report states through the GitLab API.

### Cadence.CI

`MELODIUM_API_TOKEN` is for Cadence.CI information reporting and API exchange in case of remote execution: https://cadence.ci/en/dashboard/tokens

`--build_location` and `--test_location` can either be `compose` (which makes use of local container Docker/Podman Compose command), or `api` (which pass through Cadence.CI API to connect to execution cluster): https://doc.melodium.tech/latest/en/cicd/runners/CicdDispatchEngine.html  
In both cases, the api will get reports of the execution if the `MELODIUM_API_TOKEN` is valid.

## Execute on Local

The program can be run **on** and/or **from** local.

Install `melodium` command: https://melodium.tech/en/download

`melodium run --api-report ./Compo.toml advanced --repository_clone_url "$CI_REPOSITORY_URL" --repository_clone_ref "$CI_COMMIT_REF_NAME"`

Main [entrypoint](https://doc.melodium.tech/book/en/programming/project_organization/entrypoints.html#entrypoints-parameters) can be launched with more parameters.

### Report to API

Same as for Github or GitLab run, you can set up `MELODIUM_API_TOKEN` environment variable to get execution reporting in your [Cadence.CI](https://cadence.ci) account.
