---
name: Develop in Docker with Dotfiles
description: Run workspaces on a Docker host using registry images and Dotfiles
tags: [local, docker]
icon: /icon/docker.png
---


## Getting started

Run `coder templates init` and select this template. Follow the instructions that appear.

## Editing the image

Edit the `Dockerfile` and run `coder templates push` to update workspaces.

## code-server

`code-server` is installed via the `startup_script` argument in the `coder_agent`
resource block. The `coder_app` resource is defined to access `code-server` through
the dashboard UI over `localhost:13337`.

## Extending this template

See the [kreuzwerker/docker](https://registry.terraform.io/providers/kreuzwerker/docker) Terraform provider documentation to
add the following features to your Coder template:

- SSH/TCP docker host
- Registry authentication
- Build args
- Volume mounts
- Custom container spec
- More

## How it works

During workspace creation, Coder prompts you to specify a dotfiles URL via a Terraform variable. Once the workspace starts, the Coder agent runs `coder dotfiles` via the startup script:

```hcl
variable "dotfiles_uri" {
  description = <<-EOF
  Dotfiles repo URI (optional)

  see https://dotfiles.github.io
  EOF
    # The codercom/enterprise-* images are only built for amd64
  default = ""
}

resource "coder_agent" "main" {
  ...
  startup_script = var.dotfiles_uri != "" ? "/tmp/tmp.coder*/coder dotfiles -y ${var.dotfiles_uri}" : null
}
```

# Managing images and workspaces

Refer to the documentation in the [Docker template](../docker/README.md).

