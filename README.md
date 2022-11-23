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
