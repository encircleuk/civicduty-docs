---
description: >-
  How to quickly get up and running with the CivicDuty Prefect Distro with
  Docker on Linux
---

# Getting Started

## Requirements

Assuming Docker is running on a Linux OS such as Ubuntu, Debian or Redhat.

Docker should be installed on host, including docker-compose - [Official Docker install instructions](broken-reference)

Requires the make tool to be installed on host

```bash
sudo apt -y install make
```

Requires Python 3.11.x to be installed on host

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

* Get the python packages required to build the prefect docker container

```bash
git submodule update --init --recursive
```

* Run the make file to build the prefect container from source

```bash
make docker
```

### Optional Steps

Change Postgres password in the configuration file `versions.venv` i.e.

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
