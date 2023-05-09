# Crafting Sandbox Provider

Use the Crafting Sandbox Terraform Provider to manage your organization hosted by [Crafting Sandbox](https://www.crafting.dev).
To learn more about Crafting Sandbox, please visit our [documents](https://docs.sandboxes.cloud).

## Example Usage

```terraform
terraform {
  required_providers {
    crafting = {
      source = "crafting-dev/crafting"
    }
  }
}

provider "crafting" {
}
```

With specific organization name and self-hosted server URL:

```terraform
terraform {
  required_providers {
    crafting = {
      source = "crafting-dev/crafting"
    }
  }
}

provider "crafting" {
  org = "myorg"
  server_url = "https://myorg.sandboxes.site"
}
```

## Arguments Reference

* `org` (Optional) The name of the org.
  By default, the provider will use the only org or the current one if running in a sandbox.
  It must be specified if the user who runs terraform belongs to more than one organization.
* `server_url` (Optional) The full URL of the API server. In most cases, this is automatically
  detected, even for self-hosted organization.
