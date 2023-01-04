# Resource: crafting_policy

A `crafting_policy` resource attaches a policy to a folder or org.

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

* `policy` - (Required)(string) The policy definition.
* `folder_id` - (Required)(string) The folder holding the policy. If unspecified, the policy is attached to org.

## Attributes Reference

No additional attributes except the arguments above.
