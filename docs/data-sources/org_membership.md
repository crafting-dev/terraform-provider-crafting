# Data Source: crafting_org_membership

`crafting_org_membership` can access to a specfic org membership.

## Example Usage

```terraform
data "crafting_org_membership" "s1"{
    email = "xxx@xxx.com"
}
```

## Arguments Reference

* `email` - (Required)(string) The email of the member.

## Attributes Reference

In addition to all arguments above, the following attributes are exported.

* `user_id` - (string) The user id of the membership.
* `kind` - (string) Membership kind.
* `admin` - (bool). If the member is an org-admin. Default is false.
* `disabled` - (bool). if the member is disabled. Default is false.
* `tags` - (list[string]). List of strings as tags of this member.