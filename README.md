# 29821

Reproduction for [Renovate discussion/issue #29821](https://github.com/renovatebot/renovate/discussions/29821).

## Current behavior

Only root modules that contain a `required_providers` have their lock files updated. Root modules that obtain their required provider constraints from child modules do not have their lock files updated with new constraints and package hashes. This results in an error when running any terraform command after a child module has been updated. `terraform init -upgrade` must be run first before any further commands can be executed.

In this reproduction repo, only the [`correct`](reproduction/correct) folder will have the `.terraform.lock.hcl` file updated.

## Expected behavior

The lock file should be updated for any root module to reflect the correct required provider constraints of child modules.

When fixed, the [`correct`](reproduction/correct) and [`incorrect`](reproduction/incorrect) folders will have their `.terraform.lock.hcl` files updated.

Additionally, Renovate should handle child modules from [any source (local, git, s3, etc.)](https://developer.hashicorp.com/terraform/language/modules/sources).

## Link to the Renovate issue or Discussion

A previous issue, but was closed due to a reproduction not being offered: https://github.com/renovatebot/renovate/issues/17402

Current discussion/issue: https://github.com/renovatebot/renovate/discussions/29821 
