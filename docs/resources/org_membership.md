# Resource: crafting_org_membership

A `crafting_org_membership` adds a user to the org.

## Example Usage

```terraform
resource "crafting_org_membership" "one_member" {
  email = "user1@example.com"
  admin = true
  disabled = true
  tags = ["team1", "team2"]
}
```

## Arguments Reference

* `email` - (Required)(string). User email or service account email.
* `admin` - (Optional)(bool). If the member is an org-admin. Default is false.
* `disabled` - (Optional)(bool). if the member is disabled. Default is false.
* `tags` - (Optional)(list[string]). List of strings as tags of this member.

## Attributes Reference

In addition to all arguments above, the following attributes are exported

* `kind` - (string) Membership kind.
* `user_id` - (string) The user id of the membership.