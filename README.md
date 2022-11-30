# masto-lab

Collection of Mastodon scripts

> WIP: few initial scripts

## Who is on my timeline

```shell
curl -H "Authorization: Bearer ${MASTO_TOKEN}" \
     -sS $MASTO_NODE/api/v1//timelines/public?limit=1 \
     | jq .
```

Account ID and fully qualified usernames 

```shell
curl -H "Authorization: Bearer ${MASTO_TOKEN}" \
     -sS $MASTO_NODE/api/v1/timelines/home \
     | jq '.[].account | {"id": .id, "account": .acct}' 
```

## Post new status 

```shell
curl -X POST \
     -H "Accept: application/json" \
     -H "Authorization: Bearer ${MASTO_TOKEN}" \
     -F "status"="toot with curl" \
     $MASTO_NODE/api/v1/statuses/ \
    | jq .
```