# Resource: crafting_folder

A `crafting_folder` resource creates a folder in the organization.
RBAC must be enabled to use this resource.

## Example Usage

```terraform
data "crafting_folder" "parent" {
  name   = "f1"
  folder = "eng/test"
}
resource "crafting_folder" "subfolder1" {
  name   = "subfolder1"
  folder = data.crafting_folder.parent.full_name
}
resource "crafting_folder" "subfolder2" {
  name   = "subfolder1"
  folder = "eng/test/f1"
}
```

## Arguments Reference

* `name` - (Required) The name of the folder.
* `folder` - (Optional) The path of the parent folder.

## Attributes Reference

In addition to all arguments above, the following attributes are exported:

* `id` - The object ID.
* `full_name` - The full name of the object, including folders as path.
* `owner` - The owner of the object.
    * `id` - User ID.
    * `name` - The name (email) of the user.
* `creator` - The creator of the object:
    * `id` - User ID.
    * `name` - The name (email) of the user.
* `org_id` - The org ID this object belongs to.
* `parent_id` - The ID of the containing folder.
* `labels` - The labels attached to the object. A string-to-string map.
