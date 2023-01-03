# Data Source: crafting_org

`crafting_org` can access to the current org.

## Example Usage
```terraform
data "crafting_org" "current"{
}
```

## Arguments Reference

No arguments.

## Attributes Reference

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
* `members` - (list[object]) Members in the org.
    * `user_id` - (string) User id.
    * `kind` - (string) Account kind.
    * `admin` - (string) Whether the member is admin.
    * `disabled` - (string) Whether the member is disabled.
    * `tags` - (list[string]) The tags associated with the member.
    
