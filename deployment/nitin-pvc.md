# Allow pod security privilege
```
oc adm policy add-scc-to-user anyuid -z default
```

# Create Deployment
```
oc apply -f https://raw.githubusercontent.com/nmsaini/ocp-snippets/refs/heads/master/deployment/nitin-pvc.yaml
```
# Change StorageClass (if needed)
```
oc get pvc nitin-pvc -o yaml | yq '.spec.storageClassName="new-storage-class"' | oc replace -f -
```

# Write a html file to target using terminal
```
oc rsh $(oc get po -o name -l app=nitin)
```
```
echo "
<html><body><h2>This is a test</h2></body></html>
" > /var/www/html/index.html
```

# Expose route
```
oc expose deployment nitin 
oc expose svc/nitin
```
# Test
```
curl -s $(oc get routes nitin -o jsonpath="{.spec.host}")
```
use a browser to confirm if needed

# Tear-down
```
oc delete all -l app=nitin
```
