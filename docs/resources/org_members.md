# Resource: crafting_org_members

A `crafting_org_members` resource defines a full list of memberships in the organization in the authentic way.
The existing members out of the list will be removed, except service accounts.

## Example Usage

```terraform
resource "crafting_org_members" "all_members" {
  member {
    email = "user1@example.com"
    admin = true
    disabled = false
    tags = ["team1", "team2"]
  }
  member {
    email = "user2@example.com"
    admin = true
    disabled = false
    tags = ["team1", "team2"]
  }
}
```

## Arguments Reference
* `member` - (Required) Member block.
    * `email` - (Required) User email or service account email.
    * `admin` - (Optional) If the member is an org-admin. Default is false.
    * `disabled` - (Optional) if the member is disabled. Default is false.
    * `tags` - (Optional) List of strings as tags of this member.

## Attributes Reference

In addition to all arguments above, the following attributes are exported

* `member` - The entry of a membership.
    * `kind` - Membership kind.
    * `user_id` - The ID of the user.
