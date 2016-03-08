### Sample JSON Liquibase

A sample liquibase set-up using JSON

Tags the initial structure

```sh
liquibase tag "base"
```

Creates the table 'person' in 'test' and tags the structure as 'TEST-1000'

```sh
liquibase --changeLogFile=changes/TEST-1000/changeSet.json update
```

Alters the 'person' table with the additional field 'lastname' and tags the structure as 'TEST-1001'

```sh
liquibase --changeLogFile=changes/TEST-1001/changeSet.json update
```

Imports data to the 'person' table and tags the structure as 'TEST-1002'

```sh
liquibase --changeLogFile=changes/TEST-1002/changeSet.json update
```

Drops all the data from the 'person' table and reverts to the tag 'TEST-1001'

```sh
liquibase --changeLogFile=changes/TEST-1002/changeSet.json rollback "TEST-1001"
```

Drops the 'lastname' column and reverts to the tag 'TEST-1000'

```sh
liquibase --changeLogFile=changes/TEST-1001/changeSet.json rollback "TEST-1000"
```

Drops 'person' table and reverts to the tag 'base'
```sh
liquibase --changeLogFile=changes/TEST-1000/changeSet.json rollback "base"
```
