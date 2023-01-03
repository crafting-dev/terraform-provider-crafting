# Data Source: crafting_policy

`crafting_policy` can access to a specific policy.

## Example Usage

```terraform
data "crafting_policy" "eng"{
    folder_id = crafting_folder.folder.id
}
```

## Arguments Reference
* `folder_id` - (Required)(string) The folder holding the policy. If unspecified, the policy is attached to org.

## Attributes Reference

In addition to all arguments above, the following attributes are exported.

* `policy` - (object)
    * `json` (string) The policy definition in JSON.
    * `yaml` (string) The policy definition in YAML.
