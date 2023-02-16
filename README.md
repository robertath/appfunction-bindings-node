# Azure app function using NodeJs

### Steps

#### 1. Create a function
```
func init
Use the up/down arrow keys to select a worker runtime:node
Use the up/down arrow keys to select a language:javascript

func new 
Select `Http trigger`

```

### 2. Binding `in` using cosmosdb
#### 2.1. exec Binding function
type: in
with: Azure Blob Storage
use: get Id to request document on CosmosDb


#### 2.2. Create on Azure Cosmos DB Emulator
DBName: demodb
Container: todo

#### 2.3. Start function
func start
another powershell window: Invoke-WebRequest http://localhost:7071/api/HttpTrigger?id=1


### 3. Binding `out` using cosmosdb
#### 3.1. exec Binding function
    Type: out
    with: Azure Queue Storage 
    use: 


#### 3.2. Create on Azure Queue Storage
    Use `Microsoft Azure storage explorer`
    In Emulator * Attached > Queues
    Add Queue: `outqueue`
    Change connection string of Azure storage account

#### 3.3. Start function
```
    func start
    another powershell window: Invoke-WebRequest http://localhost:7071/api/HttpTrigger?id=2
    On Azure storage explorer check outqueue if row was added.
```
