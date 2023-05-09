# Data Source: crafting_template

Use this data source to retrieve information of a Template.

## Example Usage

```terraform
data "crafting_template" "hello" {
    name = "hello"
}
```

## Arguments Reference

* `name` - (Required) The name of the template.
* `folder` - (Optional) The full path of the containing folder, if RBAC is enabled.

## Attributes Reference

In addition to all arguments above, the following attributes are exported:

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
* `labels` - The labels attached to the object. A string-to-string map.
* `definition` - The sandbox definition in YAML.
