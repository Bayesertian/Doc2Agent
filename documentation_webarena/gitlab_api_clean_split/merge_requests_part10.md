## Get single merge request changes

WARNING:
This endpoint was [deprecated](https://gitlab.com/gitlab-org/gitlab/-/issues/322117) in GitLab 15.7
and is scheduled for removal in API v5. Use the [List merge request diffs](#list-merge-request-diffs) endpoint instead.

Shows information about the merge request including its files and changes.

```plaintext
GET /projects/:id/merge_requests/:merge_request_iid/changes
```

Supported attributes:

| Attribute           | Type           | Required | Description |
|---------------------|----------------|----------|-------------|
| `id`                | integer or string | Yes      | The ID or [URL-encoded path of the project](rest/index.md#namespaced-path-encoding) owned by the authenticated user. |
| `merge_request_iid` | integer        | Yes      | The internal ID of the merge request. |
| `access_raw_diffs`  | boolean        | No       | Retrieve change diffs through Gitaly. |
| `unidiff`           | boolean        | No       | Present change diffs in the [unified diff](https://www.gnu.org/software/diffutils/manual/html_node/Detailed-Unified.html) format. Default is false. [Introduced](https://gitlab.com/gitlab-org/gitlab/-/merge_requests/130610) in GitLab 16.5. |

Diffs associated with the set of changes have the same size limitations applied as other diffs
returned by the API or viewed through the UI. When these limits impact the results, the `overflow`
field contains a value of `true`. Diff data without these limits applied can be retrieved by
adding the `access_raw_diffs` parameter, accessing diffs not from the database but from Gitaly directly.
This approach is generally slower and more resource-intensive, but isn't subject to size limits
placed on database-backed diffs. [Limits inherent to Gitaly](../development/merge_request_concepts/diffs/index.md#diff-limits)
still apply.

Example response:

```json
{
  "id": 21,
  "iid": 1,
  "project_id": 4,
  "title": "Blanditiis beatae suscipit hic assumenda et molestias nisi asperiores repellat et.",
  "state": "reopened",
  "created_at": "2015-02-02T19:49:39.159Z",
  "updated_at": "2015-02-02T20:08:49.959Z",
  "target_branch": "secret_token",
  "source_branch": "version-1-9",
  "upvotes": 0,
  "downvotes": 0,
  "author": {
    "name": "Chad Hamill",
    "username": "jarrett",
    "id": 5,
    "state": "active",
    "avatar_url": "http://www.gravatar.com/avatar/b95567800f828948baf5f4160ebb2473?s=40&d=identicon",
    "web_url" : "https://gitlab.example.com/jarrett"
  },
  "assignee": {
    "name": "Administrator",
    "username": "root",
    "id": 1,
    "state": "active",
    "avatar_url": "http://www.gravatar.com/avatar/e64c7d89f26bd1972efa854d13d7dd61?s=40&d=identicon",
    "web_url" : "https://gitlab.example.com/root"
  },
  "assignees": [{
    "name": "Miss Monserrate Beier",
    "username": "axel.block",
    "id": 12,
    "state": "active",
    "avatar_url": "http://www.gravatar.com/avatar/46f6f7dc858ada7be1853f7fb96e81da?s=80&d=identicon",
    "web_url": "https://gitlab.example.com/axel.block"
  }],
  "reviewers": [{
    "name": "Miss Monserrate Beier",
    "username": "axel.block",
    "id": 12,
    "state": "active",
    "avatar_url": "http://www.gravatar.com/avatar/46f6f7dc858ada7be1853f7fb96e81da?s=80&d=identicon",
    "web_url": "https://gitlab.example.com/axel.block"
  }],
  "source_project_id": 4,
  "target_project_id": 4,
  "labels": [ ],
  "description": "Qui voluptatibus placeat ipsa alias quasi. Deleniti rem ut sint. Optio velit qui distinctio.",
  "draft": false,
  "work_in_progress": false,
  "milestone": {
    "id": 5,
    "iid": 1,
    "project_id": 4,
    "title": "v2.0",
    "description": "Assumenda aut placeat expedita exercitationem labore sunt enim earum.",
    "state": "closed",
    "created_at": "2015-02-02T19:49:26.013Z",
    "updated_at": "2015-02-02T19:49:26.013Z",
    "due_date": null
  },
  "merge_when_pipeline_succeeds": true,
  "merge_status": "can_be_merged",
  "detailed_merge_status": "can_be_merged",
  "subscribed" : true,
  "sha": "8888888888888888888888888888888888888888",
  "merge_commit_sha": null,
  "squash_commit_sha": null,
  "user_notes_count": 1,
  "changes_count": "1",
  "should_remove_source_branch": true,
  "force_remove_source_branch": false,
  "squash": false,
  "web_url": "http://gitlab.example.com/my-group/my-project/merge_requests/1",
  "references": {
    "short": "!1",
    "relative": "!1",
    "full": "my-group/my-project!1"
  },
  "discussion_locked": false,
  "time_stats": {
    "time_estimate": 0,
    "total_time_spent": 0,
    "human_time_estimate": null,
    "human_total_time_spent": null
  },
  "task_completion_status":{
    "count":0,
    "completed_count":0
  },
  "changes": [
    {
    "old_path": "VERSION",
    "new_path": "VERSION",
    "a_mode": "100644",
    "b_mode": "100644",
    "diff": "@@ -1 +1 @@\ -1.9.7\ +1.9.8",
    "new_file": false,
    "renamed_file": false,
    "deleted_file": false
    }
  ],
  "overflow": false
}
```

