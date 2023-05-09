# Data Source: crafting_policy

Use this data source to retrieve information of a policy.
RBAC must be enabled to use this data source.

## Example Usage

```terraform
data "crafting_policy" "eng" {
    folder_id = crafting_folder.folder.id
}
```

## Arguments Reference

* `folder_id` - (Required) The folder holding the policy. If unspecified, the policy attached to the organization is used.

## Attributes Reference

In addition to all arguments above, the following attributes are exported:

* `policy` - The policy object
    * `json` The policy definition in JSON.
    * `yaml` The policy definition in YAML.
