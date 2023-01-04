# Resource: crafting_org_members

Resource `crafting_org_members` defines a full list of membership in the org in the authentic way. The existing members out of the list will be removed (except service accounts.

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
* `member` - (Required)(list[object]). Member block.
    * `email` - (Required)(string). User email or service account email.
    * `admin` - (Optional)(bool). If the member is an org-admin. Default is false.
    * `disabled` - (Optional)(bool). if the member is disabled. Default is false.
    * `tags` - (Optional)(list[string]). List of strings as tags of this member.

## Attributes Reference

In addition to all arguments above, the following attributes are exported

* `member` - (list[object]).
    * `kind` - (string) Membership kind.
    * `user_id` - (string) The user id of the membership.