# Introduction

<div class="h-lg vertical-content">

Doctrine allows you to abstract the storage into a database.

<br />

The usual Doctrine usage in Symfony consists in two layers:
* DBAL (DataBase Abstraction Layer)
* ORM (Object Relational Mapping)

</div>

---

# Configuration

<div class="h-lg vertical-content">

Open:
* .env
* config/packages/doctrine.yaml

</div>

---

# Compatibility

<div class="h-lg vertical-content">

Doctrine DBAL supports out of the box the following database systems:
* MySQL
* MariaDB
* Oracle
* Microsoft SQL Server
* PostgreSQL
* SQLite

</div>

---

# Database layer

Doctrine DBAL uses the PDO API, and is automatically installed with doctrine/orm

You can still double-check your PDO extensions to make sure you have the proper driver for your database system.

<div class="w-md h-1\/3 mx-auto vertical-content">

```bash
$ symfony php --ri pdo
```

</div>

---

# DBAL commands

<div class="h-lg vertical-content">

Doctrine ships with multiple console commands to help you automate most actions.

You can start by using the `doctrine:schema:validate --skip-mapping` command to check the connection to your database.

The `doctrine:database:create` will create a database according to your configuration, while its counterpart `doctrine:database:drop` used with the `--force` option will delete it.

</div>

---

# DBAL commands

<div class="h-lg w-xl h-1\/3 mx-auto vertical-content">

```bash
# check first
$ symfony console doctrine:schema:validate --skip-mapping

$ symfony console doctrine:database:create
$ symfony console doctrine:database:drop --force
```

</div>

---

# Exercise

<div class="h-lg vertical-content">

1. Configure Doctrine to access the database. Let’s assume we will use a SQLite storage, located in var/data.db
2. Create the database with the console

</div>
