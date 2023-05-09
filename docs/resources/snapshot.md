# Resource: crafting_snapshot 

A `crafting_snapshot` creates a snapshot in the organization.

## Examples

Base Snapshot:

```terraform
resource "crafting_snapshot" "base" {
  name = "base-dev-r1"
  type = "WORKSPACE"
  script = <<EOT
  #!/bin/bash
  apt update ...
  apt install ...
  EOT
}
``` 

Home Snapshot

```terraform
resource "crafting_snapshot" "home" {
  name = "home-dev-r1"
  type = "HOME"
  includes = [
    ".bashrc",
    ".config",
  ]
  excludes = [
    ".ssh"
  ]
  script = <<EOT
  ...
  EOT
  base_snapshot = crafting_snapshot.base.full_name
}
```

Dependency Snapshot:

```terraform
resource "crafting_snapshot" "mysql" {
  name = "mysql-dev-r1"
  type = "DEPENDENCY"
  sandbox_definition = crafting_template.hello.definition
  workload = "mysql" # The target workload to take snapshot
  workspace = "hello" # The workspace to run the script
  script = <<EOT
  ...
  EOT
}
```

Container Snapshot (only for containers with persisted volumes):

```terraform
resource "crafting_snapshot" "container" {
  name = "container-dev-r1"
  type = "CONTAINER"
  sandbox_definition = crafting_template.hello.definition
  workload = "container1" # The target workload to take snapshot
  workspace = "hello" # The workspace to run the script
  script = <<EOT
  ...
  EOT
}
```

## Arguments Reference

* `name` - (Required) The name of the snapshot.
* `folder` - (Optional)(only available when RBAC is enabled) The full path of the containing folder.
* `type` - (Required) The snapshot type, one of: `WORKSPACE`, `HOME`, `DEPENDENCY`, `CONTAINER`.
* `sandbox_definition` - Optional for `WORKSPACE`/`HOME`, required for `DEPENDENCY`/`CONTAINER`. When specified, it's used to create a sandbox for building the snapshot.
* `workspace` - Required if `script` is specified. The workspace to run the script.
* `workload` - Required for `DEPENDENCY`/`CONTAINER`, must be unspecified for `WORKSPACE`/`HOME`. The target workload to take snapshot from.
* `script` - (Optional) The script to run before taking a snapshot.
* `base_snapshot` - Only available for `HOME` snapshot without `sandbox_definition`. This is used to create the workspace.
* `includes` - Only available for `HOME` snapshot to create the includes list (this will overwrite whatever exists in the workspace).
* `excludes` - Only available for `HOME` snapshot to create the excludes list (this will overwrite whatever exists in the workspace).

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
