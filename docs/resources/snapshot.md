# Resource: crafting_snapshot 

A `crafting_snapshot` creates a snapshot in the organization.

## Examples

Workspace Snapshot

``` terraform
resource "crafting_snapshot" "base" {
  name = "base-dev-r1"
  type = "WORKSPACE"
  folder = "shared"
  script = << EOT
  #!/bin/bash
  apt update ...
  apt install ...
  EOT
}
``` 

Home Snapshot

``` terraform
resource "crafting_snapshot" "home" {
  name = "home-dev-r1"
  type = "HOME"
  folder = "shared"
  includes = [
    ".bashrc",
    ".config",
  ]
  excludes = [
    ".ssh"
  ]
  script = << EOT
  ...
  EOT
  base_snapshot = crafting_snapshot.base.full_name
}
```

Dependency Snapshot

```terraform
resource "crafting_snapshot" "mysql" {
  name = "mysql-dev-r1"
  type = "DEPENDENCY"
  app_definition = crafting_app.hello.definition
  workload = "mysql" # The target workload to take snapshot
  workspace = "hello" # The workspace to run the script
  script = << EOT
  EOT
}
```

Container Snapshot

```terraform
resource "crafting_snapshot" "container" {
  name = "container-dev-r1"
  type = "CONTAINER"
  app_definition = crafting_app.hello.definition
  workload = "container1" # The target workload to take snapshot
  workspace = "hello" # The workspace to run the script
  script = <<EOT
  EOT
}
```

## Arguments Reference
* `name` - (Required)(string) The name of the snapshot.
* `folder` - (Optional)(string) The full path of the containing folder.
* `type` - (Required)(string) The snapshot type, one of: `WORKSPACE`, `HOME`, `DEPENDENCY`, `CONTAINER`.
* `app_definition` - (Conditional)(string) Optional for `WORKSPACE`/`HOME`, required for `DEPENDENCY`/`CONTAINER`. The App Definition to create a sandbox.
* `workspace` - (Conditional)(string) Required if `app_definition` and `script` are specified. The workspace to run the script.
* `workload` - (Conditional)(string) Required for `DEPENDENCY`/`CONTAINER`, must be unspecified for `WORKSPACE`/`HOME`. The target workload to take snapshot from.
* `script` - (Optional)(string) The script to run before taking a snapshot.
* `base_snapshot` - (Conditional)(string) Only available for `HOME` snapshot without `app_definition`. This is used to create the workspace.
* `includes` - (Conditional)(list[string]) Only available for `HOME` snapshot to create the includes list (this will overwrite whatever exists in the workspace).
* `excludes` - (Conditional)(list[string]) Only available for `HOME` snapshot to create the excludes list (this will overwrite whatever exists in the workspace).

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

