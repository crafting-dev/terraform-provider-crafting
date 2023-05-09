# Resource: crafting_template

A `crafting_template` resource makes sure the specified Template is created in the organization.

## Example Usage

```terraform
resource "crafting_template" "hello" {
  name = "hello"
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

* `name` - (Required) The name of the template.
* `definition` - (Required) The sandbox definition in YAML or JSON.
* `folder` - (Optional)(only available when RBAC is enabled) The full path of the containing folder, e.g. `team1/dev`.

## Attributes Refernece.

In addition to all arguments above, the following attributes are exported

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
