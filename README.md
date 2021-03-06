# Branch Cleanup Action

[![Travis CI](https://img.shields.io/travis/jessfraz/branch-cleanup-action.svg?style=for-the-badge)](https://travis-ci.org/jessfraz/branch-cleanup-action)

A GitHub action to automatically delete the branch after a pull request has been merged. 

> **NOTE:** This will **never** delete the repository's default branch. If the pull request is closed _without_ merging, it will **not** delete it.

**Table of Contents**

<!-- toc -->

- [Usage](#usage)
- [Contributing](#contributing)
  * [Running the tests](#running-the-tests)

<!-- tocstop -->

## Usage

```
workflow "on pull request merge, delete the branch" {
  on = "pull_request"
  resolves = ["branch cleanup"]
}

action "branch cleanup" {
  uses = "elnic/branch-cleanup-action@master"
  secrets = ["GITHUB_TOKEN"]
  env = {
    BRANCH = "master"
  }
}
```

`BRANCH` environment is for specifying which master branch you used. (for example when deploying to staging it will not deleted)

![demo](demo.png)

## Contributing

### Running the tests

The tests use [shellcheck](https://github.com/koalaman/shellcheck). You don't
need to install anything. They run in a container.

```console
$ make test
```
