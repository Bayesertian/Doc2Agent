## Merge requests

The following requests are related to relationships between issues and merge requests.

### List merge requests related to issue

Gets all the merge requests that are related to the issue.

If the project is private or the issue is confidential, you need to provide credentials to authorize.
The preferred way to do this, is by using [personal access tokens](../user/profile/personal_access_tokens.md).

```plaintext
GET /projects/:id/issues/:issue_iid/related_merge_requests
```

Supported attributes:

| Attribute   | Type    | Required | Description                          |
|-------------|---------|----------|--------------------------------------|
| `id`        | integer/string | Yes      | The global ID or [URL-encoded path of the project](rest/index.md#namespaced-path-encoding) owned by the authenticated user.  |
| `issue_iid` | integer | Yes      | The internal ID of a project's issue. |

Example request:

```shell
curl --header "PRIVATE-TOKEN: <your_access_token>" \
  --url "https://gitlab.example.com/api/v4/projects/1/issues/11/related_merge_requests"
```

Example response:

```json
[
  {
    "id": 29,
    "iid": 11,
    "project_id": 1,
    "title": "Provident eius eos blanditiis consequatur neque odit.",
    "description": "Ut consequatur ipsa aspernatur quisquam voluptatum fugit. Qui harum corporis quo fuga ut incidunt veritatis. Autem necessitatibus et harum occaecati nihil ea.\r\n\r\ntwitter/flight#8",
    "state": "opened",
    "created_at": "2018-09-18T14:36:15.510Z",
    "updated_at": "2018-09-19T07:45:13.089Z",
    "closed_by": null,
    "closed_at": null,
    "target_branch": "v2.x",
    "source_branch": "so_long_jquery",
    "user_notes_count": 9,
    "upvotes": 0,
    "downvotes": 0,
    "author": {
      "id": 14,
      "name": "Verna Hills",
      "username": "lawanda_reinger",
      "state": "active",
      "avatar_url": "https://www.gravatar.com/avatar/de68a91aeab1cff563795fb98a0c2cc0?s=80&d=identicon",
      "web_url": "https://gitlab.example.com/lawanda_reinger"
    },
    "assignee": {
      "id": 19,
      "name": "Jody Baumbach",
      "username": "felipa.kuvalis",
      "state": "active",
      "avatar_url": "https://www.gravatar.com/avatar/6541fc75fc4e87e203529bd275fafd07?s=80&d=identicon",
      "web_url": "https://gitlab.example.com/felipa.kuvalis"
    },
    "source_project_id": 1,
    "target_project_id": 1,
    "labels": [],
    "draft": false,
    "work_in_progress": false,
    "milestone": {
      "id": 27,
      "iid": 2,
      "project_id": 1,
      "title": "v1.0",
      "description": "Et tenetur voluptatem minima doloribus vero dignissimos vitae.",
      "state": "active",
      "created_at": "2018-09-18T14:35:44.353Z",
      "updated_at": "2018-09-18T14:35:44.353Z",
      "due_date": null,
      "start_date": null,
      "web_url": "https://gitlab.example.com/twitter/flight/milestones/2"
    },
    "merge_when_pipeline_succeeds": false,
    "merge_status": "cannot_be_merged",
    "sha": "3b7b528e9353295c1c125dad281ac5b5deae5f12",
    "merge_commit_sha": null,
    "squash_commit_sha": null,
    "discussion_locked": null,
    "should_remove_source_branch": null,
    "force_remove_source_branch": false,
    "reference": "!11",
    "web_url": "https://gitlab.example.com/twitter/flight/merge_requests/4",
    "references": {
      "short": "!4",
      "relative": "!4",
      "full": "twitter/flight!4"
    },
    "time_stats": {
      "time_estimate": 0,
      "total_time_spent": 0,
      "human_time_estimate": null,
      "human_total_time_spent": null
    },
    "squash": false,
    "task_completion_status": {
      "count": 0,
      "completed_count": 0
    },
    "changes_count": "10",
    "latest_build_started_at": "2018-12-05T01:16:41.723Z",
    "latest_build_finished_at": "2018-12-05T02:35:54.046Z",
    "first_deployed_to_production_at": null,
    "pipeline": {
      "id": 38980952,
      "sha": "81c6a84c7aebd45a1ac2c654aa87f11e32338e0a",
      "ref": "test-branch",
      "status": "success",
      "web_url": "https://gitlab.com/gitlab-org/gitlab/pipelines/38980952"
    },
    "head_pipeline": {
      "id": 38980952,
      "sha": "81c6a84c7aebd45a1ac2c654aa87f11e32338e0a",
      "ref": "test-branch",
      "status": "success",
      "web_url": "https://gitlab.example.com/twitter/flight/pipelines/38980952",
      "before_sha": "3c738a37eb23cf4c0ed0d45d6ddde8aad4a8da51",
      "tag": false,
      "yaml_errors": null,
      "user": {
        "id": 19,
        "name": "Jody Baumbach",
        "username": "felipa.kuvalis",
        "state": "active",
        "avatar_url": "https://www.gravatar.com/avatar/6541fc75fc4e87e203529bd275fafd07?s=80&d=identicon",
        "web_url": "https://gitlab.example.com/felipa.kuvalis"
      },
      "created_at": "2018-12-05T01:16:13.342Z",
      "updated_at": "2018-12-05T02:35:54.086Z",
      "started_at": "2018-12-05T01:16:41.723Z",
      "finished_at": "2018-12-05T02:35:54.046Z",
      "committed_at": null,
      "duration": 4436,
      "coverage": "46.68",
      "detailed_status": {
        "icon": "status_warning",
        "text": "passed",
        "label": "passed with warnings",
        "group": "success-with-warnings",
        "tooltip": "passed",
        "has_details": true,
        "details_path": "/twitter/flight/pipelines/38",
        "illustration": null,
        "favicon": "https://gitlab.example.com/assets/ci_favicons/favicon_status_success-8451333011eee8ce9f2ab25dc487fe24a8758c694827a582f17f42b0a90446a2.png"
      }
    },
    "diff_refs": {
      "base_sha": "d052d768f0126e8cddf80afd8b1eb07f406a3fcb",
      "head_sha": "81c6a84c7aebd45a1ac2c654aa87f11e32338e0a",
      "start_sha": "d052d768f0126e8cddf80afd8b1eb07f406a3fcb"
    },
    "merge_error": null,
    "user": {
      "can_merge": true
    }
  }
]
```

### List merge requests that close a particular issue on merge

Gets all merge requests that close a particular issue when merged.

If the project is private or the issue is confidential, you need to provide credentials to authorize.
The preferred way to do this, is by using [personal access tokens](../user/profile/personal_access_tokens.md).

```plaintext
GET /projects/:id/issues/:issue_iid/closed_by
```

Supported attributes:

| Attribute   | Type           | Required | Description                        |
| ----------- | ---------------| -------- | ---------------------------------- |
| `id`        | integer/string | Yes      | The global ID or [URL-encoded path of the project](rest/index.md#namespaced-path-encoding) owned by the authenticated user. |
| `issue_iid` | integer        | Yes      | The internal ID of a project issue. |

Example request:

```shell
curl --header "PRIVATE-TOKEN: <your_access_token>" \
  --url "https://gitlab.example.com/api/v4/projects/1/issues/11/closed_by"
```

Example response:

```json
[
  {
    "id": 6471,
    "iid": 6432,
    "project_id": 1,
    "title": "add a test for cgi lexer options",
    "description": "closes #11",
    "state": "opened",
    "created_at": "2017-04-06T18:33:34.168Z",
    "updated_at": "2017-04-09T20:10:24.983Z",
    "target_branch": "main",
    "source_branch": "feature.custom-highlighting",
    "upvotes": 0,
    "downvotes": 0,
    "author": {
      "name": "Administrator",
      "username": "root",
      "id": 1,
      "state": "active",
      "avatar_url": "http://www.gravatar.com/avatar/e64c7d89f26bd1972efa854d13d7dd61?s=80&d=identicon",
      "web_url": "https://gitlab.example.com/root"
    },
    "assignee": null,
    "source_project_id": 1,
    "target_project_id": 1,
    "closed_at": null,
    "closed_by": null,
    "labels": [],
    "draft": false,
    "work_in_progress": false,
    "milestone": null,
    "merge_when_pipeline_succeeds": false,
    "merge_status": "unchecked",
    "sha": "5a62481d563af92b8e32d735f2fa63b94e806835",
    "merge_commit_sha": null,
    "squash_commit_sha": null,
    "user_notes_count": 1,
    "should_remove_source_branch": null,
    "force_remove_source_branch": false,
    "web_url": "https://gitlab.example.com/gitlab-org/gitlab-test/merge_requests/6432",
    "reference": "!6432",
    "references": {
      "short": "!6432",
      "relative": "!6432",
      "full": "gitlab-org/gitlab-test!6432"
    },
    "time_stats": {
      "time_estimate": 0,
      "total_time_spent": 0,
      "human_time_estimate": null,
      "human_total_time_spent": null
    }
  }
]
```

