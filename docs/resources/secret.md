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
  folder = "k8s"
  content = <<-EOT
  ...
  EOT
}
```

## Augument Reference

* `name` - (Required)(string) The name of the secret.
* `content` - (Required)(Sensitive)(string) The content of the secret.
* `folder` - (Optional)(string) The full path of the containing folder.

## Attributes Reference

* `id` - (string) The object ID.
* `full_name` - (string) The full name of the object, including folders as path.
* `owner` - (object) The owner of the object.
    * `id` - (string) User ID.
    * `name` - (string) The name (actually email) of the user.
* `creator` - (object) The creator of the object:
    * `id` - (string) User ID.
    * `name` - (string) The name (actually email) of the user.
* `org_id` - (string) The org ID this object belongs to.
* `parent_id` - (string) The ID of the containing folder.
* `labels`- (map[string,string]) The labels attached to the object.

