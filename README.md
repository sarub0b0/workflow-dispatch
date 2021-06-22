# workflow_dispatch のめも

## workflow_id

ファイル名か id を指定して実行

```
# ex. dispatch2.ymlを指定
curl --location --request POST \
  'https://api.github.com/repos/sarub0b0/workflow-dispatch/actions/workflows/dispatch2.yml/dispatches' \
  --header 'Content-Type: application/json' \
  --header 'Accept: application/vnd.github.v3+json' \
  --header 'Authorization: Bearer $GITHUB_TOKEN' \
  --data-raw '{ "ref": "main", "inputs": {} }'
```

## inputs required

`required: true` のとき default が設定されていれば、リクエストの inputs で設定されていなくてもワークフローは実行される。  
`required: true`で default が設定されていなければエラーになる。

```
{
    "message": "Required input 'required-value' not provided",
    "documentation_url": "https://docs.github.com/rest/reference/actions#create-a-workflow-dispatch-event"
}
```

| required | default    | status |
| -------- | ---------- | ------ |
| true     | define     | OK     |
| true     | not define | NG     |
| false    | define     | OK     |
| false    | not define | OK     |
