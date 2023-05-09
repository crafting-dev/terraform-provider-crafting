# Resource: crafting_org_membership

A `crafting_org_membership` resource ensures the membership of a user in the organization.

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

* `email` - (Required) User email or service account email.
* `admin` - (Optional) If the member is an org-admin. Default is false.
* `disabled` - (Optional) if the member is disabled. Default is false.
* `tags` - (Optional) List of strings as tags of this member.

## Attributes Reference

In addition to all arguments above, the following attributes are exported:

* `kind` - (string) Membership kind.
* `user_id` - (string) The ID of the user.
