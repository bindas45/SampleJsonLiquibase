### Sample JSON Liquibase

A sample liquibase set-up using JSON

#### Setting up liquibase

Here's a very basic set-up guide to get going with liquibase in Ubuntu 14.04 3.13.0-79-generic
```sh
sudo apt-get install openjdk-7-jre
sudo mkdir -p /usr/local/liquibase
cd /usr/local/liquibase
sudo wget https://github.com/liquibase/liquibase/releases/download/liquibase-parent-3.4.2/liquibase-3.4.2-bin.tar.gz
sudo tar -xvf liquibase-3.4.2-bin.tar.gz
sudo rm liquibase-3.4.2-bin.tar.gz
sudo ln -s liquibase /usr/bin/liquibase
cd ~/
git clone https://github.com/willitscale/SampleJsonLiquibase.git
cd SampleJsonLiquibase
```

### Initial Tag

Tags the initial structure as your "base" or starting point.

```sh
liquibase tag "base"
```

#### Updates

Each update should execute the defined changes and then tag the changes as outlined.

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

#### Rollbacks

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
