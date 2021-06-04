![Maintained by SeeEverything](https://img.shields.io/badge/maintained%20by-seeeverything-%6399fc.svg)

# Pre-commit hooks

This repo defines Git pre-commit hooks intended for use with [pre-commit](http://pre-commit.com/). The currently
supported hooks are:

* **terraform-fmt**: Automatically run `terraform fmt` on all Terraform code (`*.tf` files).
* **terraform-validate**: Automatically run `terraform validate` on all Terraform code (`*.tf` files).
* **tfsec**: Automatically run `tfsec` on all Terraform code (`*.tf` files).
* **tflint**: Automatically run [`tflint`](https://github.com/terraform-linters/tflint) on all Terraform code (`*.tf` files).
* **terrascan**: Automatically run `terrascan` on all Terraform code (`*.tf` files).
* **shellcheck**: Run [`shellcheck`](https://www.shellcheck.net/) to lint files that contain a bash [shebang](https://en.wikipedia.org/wiki/Shebang_(Unix)).
* **helmlint** Automatically run [`helm lint`](https://github.com/helm/helm/blob/master/docs/helm/helm_lint.md) on your Helm chart files. [See caveats here](#helm-lint-caveats).
* **markdown-link-check** Automatically run [markdown-link-check](https://github.com/tcort/markdown-link-check) on
  markdown doc files.

## General Usage

In each of your repos, add a file called `.pre-commit-config.yaml` with the following contents:

```yaml
repos:
  - repo: https://github.com/seeeverything/pre-commit
    rev: <VERSION> # Get the latest from: https://github.com/seeeverything/pre-commit
    hooks:
      - id: terraform-fmt
      - id: terraform-validate
      - id: tflint            
```

## Requirements

Depend on the hook you want to use you'll need some dependencies, below all dependencies needed to run all hooks:

* [`pre-commit`](https://pre-commit.com/#install)
* [`terraform`](https://www.terraform.io/downloads.html) required for `terraform_validate` and `terraform-fmt` hooks. Requires version `>=0.13`
* [`terraform-docs`](https://github.com/terraform-docs/terraform-docs) required for `terraform_docs` hooks.
* [`tflint`](https://github.com/terraform-linters/tflint) required for `terraform_tflint` hook.
* [`tfsec`](https://github.com/liamg/tfsec) required for `terraform_tfsec` hook.
* [`checkov`](https://github.com/bridgecrewio/checkov) required for `checkov` hook.
* [`terrascan`](https://github.com/accurics/terrascan) required for `terrascan` hook.

