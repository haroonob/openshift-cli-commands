# Build Hook 
`oc set build-hook bc/app --post-commit --script="python /opt/app-root/src/abc.py"`

`oc set build-hook bc/app --post-commit --command -- python /opt/app-root/src/abc.py`

`oc set env dc/mysql HOOK_RETRIES=5`