# dataworks-ecr-template

## Description

This is a template for creating docker images for dataworks. The flow starts from a concourse pipeline and then triggers into GHA workflow to build docker images then pushes the image into a private ECR repository.
This repo contains Makefile, Dockerfile and base terraform folders and jinja2 files to fit the standard pattern.
This repo is a base to create new non-Terraform repos, adding the githooks submodule, making the repo ready for use.

Running aviator will create the pipeline required on the AWS-Concourse instance, in order pass a mandatory CI ran status check.  this will likely require you to login to Concourse, if you haven't already.

After cloning this repo, please run:  
`make bootstrap`

In addition, you may want to do the following: 

1. Create non-default Terraform workspaces as and if required:  
    `make terraform-workspace-new workspace=<workspace_name>` e.g.  
    ```make terraform-workspace-new workspace=qa```

1. Configure Concourse CI pipeline:
    1. Add/remove jobs in `./ci/jobs` as required 
    1. Create CI pipeline:  
`aviator`