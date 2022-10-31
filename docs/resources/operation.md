---
# generated by https://github.com/hashicorp/terraform-plugin-docs
page_title: "airbyte_operation Resource - terraform-provider-airbyte"
subcategory: ""
description: |-
  Operation resource
---

# airbyte_operation (Resource)

Operation resource

## Example Usage

```terraform
resource "airbyte_workspace" "test" {
  name = "basic_test"
}

resource "airbyte_operation" "normalization" {
  workspace_id         = airbyte_workspace.test.id
  name                 = "normalization_operation"
  operator_type        = "normalization"
  normalization_option = "basic"
}

resource "airbyte_operation" "dbt" {
  workspace_id  = airbyte_workspace.test.id
  name          = "dbt_operation"
  operator_type = "dbt"
  dbt = {
    git_repo_url    = ""
    git_repo_branch = ""
    docker_image    = ""
    dbt_arguments   = ""
  }
}

resource "airbyte_operation" "webhook" {
  workspace_id  = airbyte_workspace.test.id
  name          = "webhook_operation"
  operator_type = "webhook"
  webhook = {
    execution_url     = ""
    execution_body    = ""
    webhook_config_id = ""
  }
}
```

<!-- schema generated by tfplugindocs -->
## Schema

### Required

- `name` (String) Operation Name
- `operator_type` (String) Operation Name
- `workspace_id` (String) Workspace ID

### Optional

- `dbt` (Attributes) DBT Configuration (see [below for nested schema](#nestedatt--dbt))
- `normalization_option` (String) Normalization Option
- `webhook` (Attributes) Webhook Configuration (see [below for nested schema](#nestedatt--webhook))

### Read-Only

- `id` (String) Operation ID

<a id="nestedatt--dbt"></a>
### Nested Schema for `dbt`

Required:

- `git_repo_url` (String) Git repo where DBT Transforms are

Optional:

- `dbt_arguments` (String) Arguments to pass to DBT on a run
- `docker_image` (String) DBT Docker Image
- `git_repo_branch` (String) Branch of above repo that should be used


<a id="nestedatt--webhook"></a>
### Nested Schema for `webhook`

Required:

- `execution_url` (String) The URL to call to execute the webhook operation via POST request.

Optional:

- `execution_body` (String) If populated, this will be sent with the POST request.
- `webhook_config_id` (String) The id of the webhook configs to use from the workspace.

