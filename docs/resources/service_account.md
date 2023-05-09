# Resource: crafting_service_account

A `crafting_service_account` resource creates a service account in the organization.

## Example Usage

```terraform
resource "crafting_service_account" "s1" {
    account_name = "account1"
    display_name = "Service Account 1"
}
```

## Arguments Reference

* `account_name` - (Required) The account name of the service account. It will generate the account email as `name@org.sandbox`.
* `display_name` - (Optional) The display name of the service account.

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
* `labels`- The labels attached to the object. A string-to-string map.
* `email` - The email of the service account.

