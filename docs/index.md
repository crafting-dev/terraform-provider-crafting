# Crafting Sandbox Provider

Use the Crafting Sandbox Terraform Provider to interact with the many resources supported by Crafting Sandbox.

## Example Usage

```
terraform {
  required_providers {
    crafting = {
      source = "registry.terraform.io/crafting-dev/sandbox"
    }
  }
}

provider "crafting" {
  org = "org0"
  server_url = "https://sandboxes.cloud"
}
```

## Arguments Reference
* `org` (Optional)(string) The name of the org. If unspecified, if running in a workspace, the current org is used.  Otherwise, select the only org available. If there are more than one orgs, it will report error.
* `server_url` (Optional)(string) The full URL of the API server.