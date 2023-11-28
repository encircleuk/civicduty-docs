---
description: >-
  How to quickly get up and running with the CivicDuty Prefect Distro with
  Docker on Linux
---

# 🏁 Quickstart 1 - Running The Docker Stack

Github Repo location [https://lab.civicrm.org/ttaylor/civicduty](https://lab.civicrm.org/ttaylor/civicduty)

## Requirements

Assuming Docker is running on a Linux OS such as Ubuntu, Debian or Redhat.

Docker should be installed on host, including docker-compose - [Official Docker install instructions](broken-reference)

_These instructions were derived on a host running Debian 11 (bullseye) Linux distro ._

## Step by Step Instructions

* Clone git repository from [https://lab.civicrm.org/ttaylor/civicduty](https://lab.civicrm.org/ttaylor/civicduty)

```bash
git clone https://lab.civicrm.org/ttaylor/civicduty 

```

* Navigate to newly created civicduty directory

```bash
cd civicduty
```

* Create the `.env` configuration file from the template file `versions.venv` i.e.

For x64 (Intel) machines

```bash
cp versions.env .env
```

For arm64 machines (AWS Graviton/ Mac Silicon etc)

```
cp versions-arm.env .env
```

### Optional Steps

Change Postgres password in the configuration file `.venv` i.e.

```
POSTGRES_PASSWORD=postgres-test
```



## Start the Stack

In the directory that you installed civicduty to, run the following command:

```bash
./prefect.sh start
```

By default the stack will restart after the host is rebooted



## Stop the Stack

In the directory that you installed civicduty to, run the following command:

```bash
./prefect.sh stop
```
