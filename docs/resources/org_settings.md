# Resource: crafting_org_settings

A `crafting_org_settings` update the org settings.

~> **NOTE:** At most one `crafting_org_settings` can be provided.

## Example Usage

```terraform
resource "crafting_org_settings" "settings" {
  overview = "This is a overview"
  sandbox_shared_mode = "PRIVATE"
  sandbox_always_on_expiry = 10
  favourite_apps = ["sandbox"]
  sandbox_max_idle_duration = 20
  max_pinned_sandboxes = 3
  sandbox_retention = 5
  base_images = [{"name":"ubuntu","image":"ubuntu:latest"}]
  default_base_image = "ubuntu:latest"
  onboarding = "This is a onboarding"
}
```

## Arguments Reference

* `overview` - (Optional)(string). The custom overview shown on the home page. The content is in markdown (github flavor).
* `sandbox_shared_mode` - (Optional)(string). The default sandbox shared mode. Available values are: DEFAUTL, EXPLICIT, PRIVATE.
* `sandbox_always_on_expiry` - (Optional)(int). The max duration when a sandbox is pinned, unit minute"
* `favourite_apps` - (Optional)(list[string]). The org level favourite apps.
* `sandbox_max_idle_duration` - (Optional)(int). The max duration when a sandbox is idled before being auto suspended, unit minute.
* `max_pinned_sandboxes` - (Optional)(int). The max number of pinned sandboxes.
* `sandbox_retention` - (Optional)(int). The max duration of a suspended sandbox before being deleted automatically, unit minute.
* `base_images` - (Optional)(list[object]). Optional base images.
  * `name` - (Required)(string). The name for display purpose.
  * `image` - (Required)(string). The full image name and tag.
* `default_base_image` - (Optional)(string). The container image will be used by all workspaces with 'base_snapshot' unspecified.
* `onboarding` - (Optional)(string). Guide each new user in the organization to complete a list of onboarding steps before creating sandboxes.

## Attributes Reference

All arguments above.

