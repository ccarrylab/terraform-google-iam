# Module bigquery_datasets IAM

This submodule is used to assign BigQuery dataset roles.

## Example Usage

```
module "bigquery_dataset-iam-bindings" {
  source             = "github.com/ccarrylab/terraform-gcp-module"
  project            = "level-storm-330413"
  bigquery_datasets  = ["testing2022", "anothertest"]
  mode               = "additive"

  bindings = {
    "roles/bigquery.dataViewer" = [
      "serviceAccount:bigquery@level-storm-330413.iam.gserviceaccount.com",
      "group:my-group@my-org.com",
      "user:cohen.carryl@gmail.com",
    ]
    "roles/bigquery.dataEditor" = [
      "serviceAccount:bigquery@level-storm-330413.iam.gserviceaccount.com",
      "group:my-group@my-org.com",
      "user:cohen.carryl@gmail.com",
    ]
  }
}
```

<!-- BEGINNING OF PRE-COMMIT-TERRAFORM DOCS HOOK -->

## Inputs

| Name              | Description                                                                    | Type           | Default      | Required |
| ----------------- | ------------------------------------------------------------------------------ | -------------- | ------------ | :------: |
| bigquery_datasets | BigQuery dataset IDs list to add the IAM policies/bindings                     | `list(string)` | n/a          |   yes    |
| bindings          | Map of role (key) and list of members (value) to add the IAM policies/bindings | `map(any)`     | n/a          |   yes    |
| mode              | Mode for adding the IAM policies/bindings, additive and authoritative          | `string`       | `"additive"` |    no    |
| project           | Project to add the IAM policies/bindings                                       | `string`       | n/a          |   yes    |

## Outputs

| Name              | Description                                        |
| ----------------- | -------------------------------------------------- |
| bigquery_datasets | Bigquery dataset IDs which received for bindings.  |
| members           | Members which were bound to the bigquery datasets. |
| roles             | Roles which were assigned to members.              |

<!-- END OF PRE-COMMIT-TERRAFORM DOCS HOOK -->
