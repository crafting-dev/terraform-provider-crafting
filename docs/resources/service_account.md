# Resource: crafting_service_account

`crafting_service_account` creates a service account in the org.

## Example Usage

```terraform
resource "crafting_service_account" "s1"{
    account_name = "account1"
    display_name = "Service Account 1"
}
```

## Arguments Reference

* `account_name` - (Required)(string) The account name of the service account.
* `display_name` - (Optional)(string) The display name of the service account.

## Attributes Reference

In addition to all arguments above, the following attributes are exported.

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

