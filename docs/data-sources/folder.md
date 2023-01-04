# Data Source: crafting_folder

`crafting_folder` can access to a specific folder.

## Example Usage

``` terraform
data "crafting_folder" "parent"{
    name = "f1"
    folder = "sandbox/frontend"
}
```

## Arguments Reference

* `name` - (Required)(string) The name of the app.
* `folder` - (Optional)(string) The full path of the containing folder.

## Attributes Reference

In addition to all arguments above, the following attributes are exported.

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


