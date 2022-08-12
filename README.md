# file-existence-action

> GitHub Action to check for file existence

![build-test](https://github.com/department-for-transport/file-existence-action/workflows/build/badge.svg)

This is a GitHub Action to check for existence of file types which you don't want to be present in your repo. It will flag up as a failure and send you an email if it spots a problem. 

## Usage

The following example [workflow step](https://help.github.com/en/actions/configuring-and-managing-workflows/configuring-a-workflow) will check for existence of the files: `package.json`, `LICENSE`, `README.md`, `foo` `bar`

```yml
- name: "Check file existence"
  uses: department-for-transport/file-existence-action@v2
  with:
    files: "xlsx, csv"
```

## Outputs
- `files_exists`: Outputs `false` if one or more of the listed file types exist, otherwise `true`.

