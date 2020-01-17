# Bumping Major Version Number

This document outlines the process for bumping the major version of Chef Infra Client for the yearly release.

## Preparing Ohai

Chef consumes Ohai from GitHub in both the Gemfile and in buildkite jobs that perform Test Kitchen runs. The first step in bumping the major release in the chef/chef repo is to bump the major version of Ohai.

### Add a stable branch to Ohai

On your local machine fork the current master branch to a new stable branch. For example: `git checkout -b 15-stable`. You’ll then want to edit the Expeditor config.yml file to update the branch configs like this:

https://github.com/chef/ohai/commit/ad208165619425dd7886b2de3f168b49ded25146

With the expeditor config complete push the branch `git push --set-upstream origin 15-stable`

### Bump Ohai master to the new major

Edit the `VERSION` file in the root of the repository to the new major release and create a Pull Request

Example PR:

https://github.com/chef/ohai/pull/1420

## Fork Chef master to a stable branch

The first step in releasing a new major version of Chef Infra Client is forking the current contents of the master branch to a stable branch, which will be used to build hotfix releases. We support the N-1 version of Chef Infra Client for a year after the release of a new major version. For example Chef Infra Client 16 was released in April 2020, at which point Chef Infra Client 15 became the N-1 release. Chef Infra Client 15 will then be maintained with critical bug and security fixes until April 2021.

## Configure Expeditor to build the branch

Update the expeditor config at https://github.com/chef/chef/blob/master/.expeditor/config.yml to include a release branch for the stable version.
