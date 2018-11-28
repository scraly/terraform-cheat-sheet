# Terraform Cheat Sheet

## Installation

### Install through curl

```
$ curl -O https://releases.hashicorp.com/terraform/0.11.10/terraform_0.11.10_linux_amd64.zip
$ sudo unzip terraform_0.11.10_linux_amd64.zip -d /usr/local/bin/
$ rm terraform_0.11.10_linux_amd64.zip
```

### OR install through tfenv: a Terraform version manager

```
$ git clone https://github.com/Zordrak/tfenv.git ~/.tfenv
$ echo 'export PATH="$HOME/.tfenv/bin:$PATH"' >> $HOME/bashrc
```

### Show version

$ terraform --version
 
Terraform v0.11.10

## Usage

### Init Terraform

`$ terraform init`

The command terraform init will install :

terraform modules
eventually a backend
and provider(s) plugins

### Change backend configuration during the init

`terraform init -backend-config=cfg/s3.${params.target}.tf -reconfigure`

### Get

This command is useful when you have defined some modules.
Modules are vendored so when you edit them, you need to get again modules content.

`$ terraform get -update=true`

When you use modules, the first thing you’ll have to do is to do a terraform get. This pulls modules into the .terraform directory. Once you do that, unless you do another terraform get -update=true, you’ve essentially vendored those modules.

### Plan

The plan step check configuration to execute and write a plan to apply to target infrastructure provider.

`$ terraform plan -out plan.out`

It's an important feature of Terraform that allows a user to see which actions Terraform will perform prior to making any changes, increasing confidence that a change will have the desired effect once applied. 

When you execute terraform plan command, terraform will scan all *.tf files in your directory and create the plan.

### Apply

Now you have the desired state so you can execute the plan.

`$ terraform apply plan.out`

**Good to know:**
Since terraform v0.11+, in an interactive mode (non CI/CD/autonomous pipeline), you can just excute terraform apply command which will print out which actions TF will perform.

By generating the plan and applying it in the same command, Terraform can guarantee that the execution plan won't change, without needing to write it to disk. This reduces the risk of potentially-sensitive data being left behind, or accidentally checked into version control.

`$ terraform apply`

### Apply and auto aprove

`$ terraform apply -auto-aprove`

## Workspaces

To manage multiple distinct sets of infrastructure resources/environments.

Instead of create a directory for each environment to manage, we need to just create needed workspace and use them:

### Create workspace

This command create a new workspace and then select it

`$ terraform workspace new dev`

### Select a workspace

`$ terraform workspace select dev`

### List workspaces

```
$ terraform workspace list
  default
* dev
  prelive
```

