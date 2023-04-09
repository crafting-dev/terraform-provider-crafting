# Resource: crafting_template

An `crafting_template` resource makes sure the corresponding Template is created in the organization


## Example Usage

``` terraform
resource "crafting_template" "hello" {
  name = "hello"
  folder = "a/b/c"
  definition = <<-EOT
  ---
  workspaces:
  - name: hello
    checkouts:
      - path: src/hello
        repo:
          git: git@github.com:crafting-dev/hello
  EOT
}
```

## Arguments Reference

The following arguments are supported:

* `name` - (Required)(string) The name of the template.
* `definition` - (Required)(string) The template definition in YAML or JSON.
* `folder` - (Optional)(string) The full path of the containing folder.

## Attributes Refernece.

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

