# Data Source: crafting_service_account

Use this data source to retrieve information of a Service Account.

## Example Usage

```terraform
data "crafting_service_account" "a1" {
    account_name "account1"
}
data "crafting_service_account" "a2" {
    email =  "account2@org.sandbox"
}
```

## Arguments Reference

* `account_name` - (Optional) The account name of the service account. If specified, the `email` must be unspecified.
* `email` - (Optional) The email of the service account. If specified, the `account_name` must be unspecified.

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
* `email` - The email of the service account.
* `display_name` - The display name of the service account.
