## List forks of a project

List the projects accessible to the calling user that have an established,
forked relationship with the specified project

```plaintext
GET /projects/:id/forks
```

| Attribute                     | Type              | Required | Description |
|-------------------------------|-------------------|----------|-------------|
| `id`                          | integer or string | Yes      | The ID or [URL-encoded path of the project](rest/index.md#namespaced-path-encoding). |
| `archived`                    | boolean           | No       | Limit by archived status. |
| `membership`                  | boolean           | No       | Limit by projects that the current user is a member of. |
| `min_access_level`            | integer           | No       | Limit by current user minimal [role (`access_level`)](members.md#roles). |
| `order_by`                    | string            | No       | Return projects ordered by `id`, `name`, `path`, `created_at`, `updated_at`, or `last_activity_at` fields. Default is `created_at`. |
| `owned`                       | boolean           | No       | Limit by projects explicitly owned by the current user. |
| `search`                      | string            | No       | Return list of projects matching the search criteria. |
| `simple`                      | boolean           | No       | Return only limited fields for each project. Without authentication, this operation is a no-op; only simple fields are returned. |
| `sort`                        | string            | No       | Return projects sorted in `asc` or `desc` order. Default is `desc`. |
| `starred`                     | boolean           | No       | Limit by projects starred by the current user. |
| `statistics`                  | boolean           | No       | Include project statistics. Available only to users with at least the Reporter role. |
| `updated_after`               | datetime          | No       | Limit results to projects last updated after the specified time. Format: ISO 8601 (`YYYY-MM-DDTHH:MM:SSZ`). [Introduced](https://gitlab.com/gitlab-org/gitlab/-/issues/393979) in GitLab 15.10. |
| `updated_before`              | datetime          | No       | Limit results to projects last updated before the specified time. Format: ISO 8601 (`YYYY-MM-DDTHH:MM:SSZ`). [Introduced](https://gitlab.com/gitlab-org/gitlab/-/issues/393979) in GitLab 15.10. |
| `visibility`                  | string            | No       | Limit by visibility `public`, `internal`, or `private`. |
| `with_custom_attributes`      | boolean           | No       | Include [custom attributes](custom_attributes.md) in response. _(administrators only)_ |
| `with_issues_enabled`         | boolean           | No       | Limit by enabled issues feature. |
| `with_merge_requests_enabled` | boolean           | No       | Limit by enabled merge requests feature. |

```shell
curl --header "PRIVATE-TOKEN: <your_access_token>" "https://gitlab.example.com/api/v4/projects/5/forks"
```

Example responses:

```json
[
  {
    "id": 3,
    "description": "Lorem ipsum dolor sit amet, consectetur adipiscing elit.",
    "description_html": "<p data-sourcepos=\"1:1-1:56\" dir=\"auto\">Lorem ipsum dolor sit amet, consectetur adipiscing elit.</p>",
    "default_branch": "main",
    "visibility": "internal",
    "ssh_url_to_repo": "git@example.com:diaspora/diaspora-project-site.git",
    "http_url_to_repo": "http://example.com/diaspora/diaspora-project-site.git",
    "web_url": "http://example.com/diaspora/diaspora-project-site",
    "readme_url": "http://example.com/diaspora/diaspora-project-site/blob/main/README.md",
    "tag_list": [ //deprecated, use `topics` instead
      "example",
      "disapora project"
    ],
    "topics": [
      "example",
      "disapora project"
    ],
    "name": "Diaspora Project Site",
    "name_with_namespace": "Diaspora / Diaspora Project Site",
    "path": "diaspora-project-site",
    "path_with_namespace": "diaspora/diaspora-project-site",
    "repository_object_format": "sha1",
    "issues_enabled": true,
    "open_issues_count": 1,
    "merge_requests_enabled": true,
    "jobs_enabled": true,
    "wiki_enabled": true,
    "snippets_enabled": false,
    "can_create_merge_request_in": true,
    "resolve_outdated_diff_discussions": false,
    "container_registry_enabled": false, // deprecated, use container_registry_access_level instead
    "container_registry_access_level": "disabled",
    "security_and_compliance_access_level": "disabled",
    "created_at": "2013-09-30T13:46:02Z",
    "updated_at": "2013-09-30T13:46:02Z",
    "last_activity_at": "2013-09-30T13:46:02Z",
    "creator_id": 3,
    "namespace": {
      "id": 3,
      "name": "Diaspora",
      "path": "diaspora",
      "kind": "group",
      "full_path": "diaspora"
    },
    "import_status": "none",
    "archived": true,
    "avatar_url": "http://example.com/uploads/project/avatar/3/uploads/avatar.png",
    "shared_runners_enabled": true,
    "group_runners_enabled": true,
    "forks_count": 0,
    "star_count": 1,
    "public_jobs": true,
    "shared_with_groups": [],
    "only_allow_merge_if_pipeline_succeeds": false,
    "allow_merge_on_skipped_pipeline": false,
    "restrict_user_defined_variables": false,
    "only_allow_merge_if_all_discussions_are_resolved": false,
    "remove_source_branch_after_merge": false,
    "request_access_enabled": false,
    "merge_method": "merge",
    "squash_option": "default_on",
    "autoclose_referenced_issues": true,
    "enforce_auth_checks_on_uploads": true,
    "suggestion_commit_message": null,
    "merge_commit_template": null,
    "container_registry_image_prefix": "registry.example.com/diaspora/diaspora-project-site",
    "_links": {
      "self": "http://example.com/api/v4/projects",
      "issues": "http://example.com/api/v4/projects/1/issues",
      "merge_requests": "http://example.com/api/v4/projects/1/merge_requests",
      "repo_branches": "http://example.com/api/v4/projects/1/repository_branches",
      "labels": "http://example.com/api/v4/projects/1/labels",
      "events": "http://example.com/api/v4/projects/1/events",
      "members": "http://example.com/api/v4/projects/1/members",
      "cluster_agents": "http://example.com/api/v4/projects/1/cluster_agents"
    }
  }
]
```

