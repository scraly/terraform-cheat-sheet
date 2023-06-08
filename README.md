# Terraform cheat sheet

# Generate cheat sheet PDF

`$ ./bin/asciidoctorjs-pdf terraform-cheat-sheet.adoc --template-require ../examples/cheat-sheet/template/template.js`

# WIP

## Other useful commands

Inspect what is currently in the TF state (useful after an apply)
```
$ terraform show
```

Set the log to DEBUG level and save the log in an output external file
```
$ TF_LOG_PATH=mylogfile.txt TF_LOG=debug terraform apply
```

Refresh information. Compare the current real remote information and put it in the TF state

```
$ terraform refresh
```

Get an element from a slice
(convert a set to a list and then get the first element in the list)

```
https://developer.hashicorp.com/terraform/language/functions/tolist

output "iam" {
    value = data.ovh_iam_policies.my_policies.policies
}

Outputs:

iam = toset([
  "1a016c5f-bb43-4069-803d-daab0f22319b",
  "d7daf48e-ba7e-4373-aa4b-b6a9dcace1f3",
])

data "ovh_iam_policy" "my_policy" {
  id = tolist(data.ovh_iam_policies.my_policies.policies)[0]
}
```

Display all the available resources in your TF state

```
terraform state list
```

Output:

```
data.ovh_iam_policies.my_policies
data.ovh_iam_policy.my_policy
data.ovh_iam_reference_actions.vps_actions
```
