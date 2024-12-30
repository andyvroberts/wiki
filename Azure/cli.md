## Azure CLI

### RBAC Custom Role



### Storage Queue
List all storage queues in the storage account.
```
export storeacc=uklandregappdata
export prefix=landreg

az storage queue list --prefix $prefix --account-name $storeacc
```
To capture just the names in a file
```
az storage queue list --prefix $prefix --account-name $storeacc --query "[].name" -o tsv > qlist.txt
```

Delete a single named queue.
```
export name=landreg-b5

az storage queue delete -n $name --fail-not-exist --account-name $storeacc
```
In cases where there might bea large number of Queue's, deleting them individually can be slow.  To delete every Queue, combine a list and delete operation using linux bash xargs command.
```
az storage queue list --prefix $prefix --account-name $storeacc --query "[].name" -o tsv | xargs -L1 -P10 -I{} az storage queue delete --fail-not-exist --account-name $storeacc -n {}
``