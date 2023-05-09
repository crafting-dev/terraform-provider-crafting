# Data Source: crafting_org_membership

Use this data source to retrieve information of a specfic membership in the organization.

## Example Usage

```terraform
data "crafting_org_membership" "s1" {
    email = "foo@bar.com"
}
```

## Arguments Reference

* `email` - (Required) The email of the member.

## Attributes Reference

In addition to all arguments above, the following attributes are exported:

* `user_id` - The user id of the membership.
* `kind` - Membership kind.
* `admin` - If `true`, the member is an org-admin.
* `disabled` - If `true`, the member is disabled.
* `tags` - List of strings as tags of this member.
