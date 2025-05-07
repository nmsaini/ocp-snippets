# allow pod security privilege
```
oc adm policy add-scc-to-user anyuid -z default
```

# create deployment
```
oc apply -f nitin-pvc.yaml
```

# write a html file to target
```
echo "
<html><body><h2>This is a test</h2></body></html>
" > /var/www/html/index.html
```

# expose route
```
oc expose deployment nitin 
oc expose svc/nitin
```
# test
```
curl -s $(oc get routes nitin -o jsonpath="{.spec.host}")
```

# tear down
```
oc delete all -l app=nitin
```
