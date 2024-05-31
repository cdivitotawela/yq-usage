# yq-usage
This repository provide some useful information about the usage of yq tool

## Update a field value selectively
Following yml file contains a dictionary of users and need to update status for the user name2. In order to select the values, dictionary need to be converted to a list using `to_entries`.

```yaml
# file.yml
users:
  name1:
    status: active
  name2:
    status: inactive
```

```sh
yq -i '(.users | to_entries | .[] | select(.key == "name2").value.status) = "active"' file.yml
```
