# yq-usage
This repository provide some useful information about the usage of yq tool

## Update a field value selectively
Following yml file contains a dictionary of users and need to update status for the user name2. In order to select the values, dictionary need to be converted to a list using `to_entries`. Option `-i` used to update the file in-place.

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

## Examples in GitHub actions

| Workflow                                     | Description                                                                               |
|----------------------------------------------|-------------------------------------------------------------------------------------------|
| [example01](.github/workflows/example01.yml) | Extract fileds from complex data structure. Data structure contains key names with dashes |
