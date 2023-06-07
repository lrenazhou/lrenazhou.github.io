---
title: "Datadog take-home assignment"
date: 2021-02-16T12:08:55-08:00
draft: false

---

## Exercise 1: Collecting Metrics

1. ![Host Map with tags](/images/1_1_hostmap_tags.png)
2. Postgres `conf.yaml`: 

```
init_config:

instances:
  ## @param host - string - required
  ## The hostname to connect to.
  ## NOTE: Even if the server name is "localhost", the agent connects to
  ## PostgreSQL using TCP/IP, unless you also provide a value for the sock key.
  #
  - host: localhost

    ## @param port - integer - required
    ## Port to use when connecting to PostgreSQL.
    #
    port: 5432

    ## @param user - string - required
    ## Datadog Username created to connect to PostgreSQL.
    #
    username: datadog

    ## @param pass - string - required
    ## Password associated with the Datadog user.
    #
    password: "datadogcandidate"

    ## @param dbname - string - optional - default: postgres
    ## Name of the PostgresSQL database to monitor.
    ## Note: If omitted, the default system postgres database is queried.
    #
    # dbname: "<DB_NAME>"

    # @param disable_generic_tags - boolean - optional - default: false
    # The integration will stop sending server tag as is reduntant with host tag
    disable_generic_tags: true
```
Postgres integration dashboard: 
![Postgres integration dashboard](/images/1_2_postgres_integration_dashboard.png)

3. `custom_my_metric.yaml`:

```
init_config:

instances:
  - min_collection_interval: 45
 ```

`custom_my_metric.py`:

```
import random 

# the following try/except block will make the custom check compatible with any Agent version
try:
    # first, try to import the base class from new versions of the Agent...
    from datadog_checks.base import AgentCheck
except ImportError:
    # ...if the above failed, the check is running in Agent version < 6.6.0
    from checks import AgentCheck

# content of the special variable __version__ will be shown in the Agent status page
__version__ = "1.0.0"

class CustomMyMetricCheck(AgentCheck):
    def check(self, instance):
        random_num = random.randint(1,100)
        self.gauge('my_metric', random_num)
```

4. ![my_metric interval change](/images/1_4_my_metric_interval_change.png)
5. You modify the `min_collection_interval` parameter in the Agent check `yaml` file.

## Exercise 2: Visualizing Data

1. 
2. 
3. 
4. 

## Exercise 3: Getting Started