# OData User Synchroniser
Synchronise users between instances of the DHuS.

## How to use

### Set the environment variables that configure the DHuS:

+ **DHOST** DHuS Host address eg: localhost:8080, scihub.copernicus.eu/dhus/
+ **DLOGIN** DHuS login username to connect to the $DHOST DHuS
+ **DPASS** DHuS login password to connect to the $DHOST DHuS

### Commands

Parameters between angle brackets (chevrons) are mandatory.

Parameters between brackets ([]) are optional.

Create a Synchroniser:  
```
./createSynchronizer
    <-D_SCHEDULE=cron_expression>
    <-D_SERVICEURL=URL_to_remote_DHuS_to_sync>
    <-D_SERVICELOGIN=account>
    <-D_SERVICEPASSWORD=password>
    [-D_LABEL=my_sync]
    [-D_PAGESIZE=X]
    [-D_REQUEST=start|stop]
    [-D_CURSOR=position]
    [-D_FORCE=true|false]
```

List synchronisers / print a synchroniser:
```
./getSynchronizer [synchroniser id [URI parameters]]
```

Delete a synchroniser:
```
./deleteSynchronizer <synchroniser id>
```

Update a synchroniser:
```
./updateSynchronizer <synchroniser id> [any options accepted by createSynchronizer]
```

There are options to nullify nullable properties: -D_LABEL_NULL

Start a synchroniser:
```
./startSync <synchroniser id>
```

Stop a synchroniser:
```
./stopSync <synchroniser id>
```

### Examples

```bash
./createSynchronizer -D_LABEL=my_user_syncer \
      -D_SERVICEURL="http://dhus1:8080/odata/v1" -D_SERVICELOGIN=root -D_SERVICEPASSWORD=rootpassword \
      -D_SCHEDULE="0 */3 * * * ?" -D_REQUEST=stop
```
