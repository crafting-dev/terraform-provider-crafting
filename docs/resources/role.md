# Resource: crafting_role

A `crafting_role` resource defines a custome role.
RBAC must be enabled to use this resource.

## Example Usage

``` terraform
resource "crafting_role" "role1" {
  name = "custom-role1"
  access_rule {
    object = {
      kinds = ["Sandbox", "Template"]
    }
    actions = ["view", "access"]
  }
}
```

## Arguments Reference

* `name` - (Required) The name of the role.
* `folder` - (Optional) The full path of the containing folder.
* `access_rule` (Optional) Access rules block.
    * `object` (Optional)
        * `kinds` (Optional) A list of object kinds.
    * `actions` (Required) One or more actions to be matched.

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
* `labels`- The labels attached to the object. A string-to-string map.

