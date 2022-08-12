# file-existence-action

> GitHub Action to check for file existence

![build-test](https://github.com/department-for-transport/file-existence-action/workflows/build/badge.svg)

This is a GitHub Action to check for existence of file types which you don't want to be present in your repo. It will flag up as a failure and send you an email if it spots a problem. 

## Usage

The following example [workflow step](https://help.github.com/en/actions/configuring-and-managing-workflows/configuring-a-workflow) will check for existence of the files: `package.json`, `LICENSE`, `README.md`, `foo` `bar`

```yml
- name: Check file existence
        id: check_files
        uses: department-for-transport/file-existence-action@v5
        with:
          files: "*xlsx, *csv"

      - name: File exists
        if: steps.check_files.outputs.files_exists == 'true'
        # Only runs if any of the file types exist
        run: |
          echo "Error: following file types found ${{ steps.check_files.outputs.missing_files }}"
          exit 1
```

## Outputs
- `files_exists`: Outputs `false` if one or more of the listed file types exist, otherwise `true`.

