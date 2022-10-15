# Change Deployment strategy from rolling to recreate
## remove trigger 
`oc set triggers dc/mysql --from-config --remove`
## change strategy 
`oc patch dc/mysql --patch '{"spec":{"strategy":{"type":"Recreate"}}}'`
`oc patch dc/mysql --type=json -p='[{"op":"remove", "path": "/spec/strategy/rollingParams"}]'`

## reenabled trigger
`oc set triggers dc/name --auto`