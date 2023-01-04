# Data Source: crafting_service_account

`crafting_service_account` can access a specific service account.

## Example Usage

```terraform
data "crafting_service_account" "a1"{
    account_name "account1"
}
data "crafting_service_account" "a2"{
    email =  "account2@org.sandbox"
}
```

## Arguments Reference

* `account_name` - (Optional)(string). The account name of the service account. If specified, the `email` must  be unspecified.
* `name` - (Optional)(string). The name of the service account(Actually email). If specified, the `account_name` must be unspecified.

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
* `email` - (string) The email of the service account.
* `display_name` - (string) The email of the display_name.