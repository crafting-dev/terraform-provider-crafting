# Resource: crafting_policy

A `crafting_policy` resource attaches a policy to a folder or organization.
RBAC must be enabled to use this resource.

## Example

```terraform
resource "crafting_policy" "eng" {
  folder_id = crafting_folder.folder.id
  policy    = <<-EOT
  YAML or JSON
  EOT
}
```

## Arguments Reference

* `policy` - (Required) The policy definition.
* `folder_id` - (Required) The folder holding the policy. If unspecified, the policy is attached to the organization.

## Attributes Reference

No additional attributes except the arguments above.
