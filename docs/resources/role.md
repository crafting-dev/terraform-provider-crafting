# Resource: crafting_role

A `crafting_role` resource defines a custome role.

## Example Usage

``` terraform
resource "crafting_role" "role1" {
  name = "custom-role1"
  folder = "backend/teamA"
  access_rule {
    object = {
      kinds = ["Sandbox", "App"]
    }
    actions = ["view", "access"]
  }
}
```

## Arguments Reference

* `name` - (Required)(string) The name of the role.
* `folder` - (Optional)(string) The full path of the containing folder.
* `access_rule` (Optional)(list[object]) Access rules block.
    * `object` (Optional)(list[object])
        * `kinds` (Optional)(list[string])  Kind of the object.
    * `actions` (Required)(list[string]) One or more actions to be matched.

## Attributes Reference

In addition to all arguments above, the following attributes are exported

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

