# Resource: crafting_secret

A `crafting_secret` resource creates a secret in the organization.

<!---
Below is a note
-->
-> The provider only supports shared secrets.


## Example 

``` terraform
resource "crafting_secret" "kubeconfig" {
  name = "kubeconfig.yaml"
  content = <<-EOT
  ...
  EOT
}
```

## Augument Reference

* `name` - (Required) The name of the secret.
* `content` - (Required)(Sensitive) The content of the secret.
* `folder` - (Optional) The full path of the containing folder, if RBAC is enabled.

## Attributes Reference

* `id` - The object ID.
* `full_name` - The full name of the object, including folders as path, if RBAC is enabled.
* `owner` - The owner of the object.
    * `id` - User ID.
    * `name` - The name (email) of the user.
* `creator` - The creator of the object:
    * `id` - User ID.
    * `name` - The name (email) of the user.
* `org_id` - The org ID this object belongs to.
* `parent_id` - The ID of the containing folder, if RBAC is enabled.
* `labels`- The labels attached to the object. A string-to-string map.
