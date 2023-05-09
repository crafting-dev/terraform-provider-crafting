# Resource: crafting_org_settings

A `crafting_org_settings` resource updates the organizational settings.

~> **NOTE:** At most one `crafting_org_settings` resource can be defined.

## Example Usage

```terraform
resource "crafting_org_settings" "settings" {
  overview = <<-EOT
  This is an overview markdown document, showing at home page.
  EOT
  sandbox_shared_mode = "PRIVATE"
  sandbox_always_on_expiry = 10
  favourite_templates = ["sandbox"]
  sandbox_max_idle_duration = 20
  max_pinned_sandboxes = 3
  sandbox_retention = 5
  base_images = [{"name":"ubuntu","image":"ubuntu:latest"}]
  default_base_image = "ubuntu:latest"
  onboarding = <<-EOT
  This is an onboarding guidance markdown document.
  EOT
}
```

## Arguments Reference

* `overview` - (Optional) The custom overview shown on the home page. The content is in markdown (github flavor).
* `sandbox_shared_mode` - (Optional) The default sandbox shared mode. Available values are: `DEFAULT`, `PRIVATE`.
* `sandbox_always_on_expiry` - (Optional) The max duration when a sandbox is pinned, in minutes.
* `favourite_templates` - (Optional) A list of templates shown as favourite at the organization level.
* `sandbox_max_idle_duration` - (Optional) The max duration when a sandbox is idled before being suspended, in minutes.
* `max_pinned_sandboxes` - (Optional) The max allowed number of pinned sandboxes.
* `sandbox_retention` - (Optional) The max duration of a suspended sandbox before being deleted automatically, in minutes.
* `base_images` - (Optional) A list of container images can be selected as base snapshot when creating sandboxes.
  * `name` - (Required) The display name of the image.
  * `image` - (Required) The full image name and tag.
* `default_base_image` - (Optional) The container image (full image name and tag) will be used by all workspaces if 'base_snapshot' is unspecified.
* `onboarding` - (Optional) Guide each new user in the organization to complete a list of onboarding steps before creating sandboxes, in markdown (github flavor).

## Attributes Reference

All arguments above.
