# My Personal pre-commits

### Requirements txt fixer

This pre-commit has been taken form the original pre-commit ```github.com/pre-commit/pre-commit-hooks``` with added code check to see the requirements versions has == instead of =, if it finds a single = it will fix if for you.

### tf-module-checker

This pre-commit will check your terraform modules sources to make sure you are not using lastest as a ref e.g ```git::git@github.com:repo/terraform-modules.git//folder/folder/module-folder?ref=latest"```


### tf-cache-cleanup

This pre-commit will clean up your terraform cache


#### Example of .pre-commit-config.yaml file using terraform

default_stages: [push]
repos:
  - repo: https://github.com/RyanD0001/pre-commit
    rev: v0.0.1 #use the latest release
    hooks:
      - id: tf-module-checker
        files: '.*(.tf|.tfvars)'
        exclude: '(.terragrunt-cache/|.terraform/|.terraform.lock|examples/)'
        stages: [commit]
        
        
#### Example of .pre-commit-config.yaml file using python
  - repo: https://github.com/RyanD0001/pre-commit
    rev: v0.0.1 #use the latest release
    hooks:
      - id: requirements-txt-fixer
        stages: [commit]
