# Data Source: crafting_folder

Use this data source to retrieve information of a folder.

## Example Usage

``` terraform
data "crafting_folder" "parent" {
    name = "f1"
    folder = "sandbox/frontend"
}
```

## Arguments Reference

* `name` - (Required) The name of the folder.
* `folder` - (Optional) The full path of the parent folder.

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
