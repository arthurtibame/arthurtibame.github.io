---
title: "Airflow Dags"
date: 2021-01-05T08:21:25+08:00
hero: /posts/data_engineer/airflow/installation/airflow.svg
description: Dags of airflow
menu:
  sidebar:
    name: Dags
    identifier: airflow-dags
    parent: airflow
    weight: 10
---

## Airflow Contents
1. [Installation](https://arthurtibame.github.io/posts/data_engineer/airflow/installation/)
2. [Dags]((https://arthurtibame.github.io/posts/data_engineer/airflow/dags/))

## What is DAG
Directed Acyclic Graph (DAG)

1. Directed - If multiple tasks exist, each must have at least one defined upstream (previous) or downstream (subsequent) tasks, although they could easily have both.
2. Acyclic - No task can create data that goes on to reference itself. This could cause an infinite loop that would be, um, it’d be bad. Don’t do that.
3. Graph - All tasks are laid out in a clear structure with discrete processes occurring at set points and clear relationships made to other tasks.


---
### Learning from an [exmaple](https://airflow.apache.org/docs/apache-airflow/stable/tutorial.html)

### Step 1. Import required library
```python
from airflow import DAG
```
### Step 2. Define our default arguments with dicttionary (optional)
```python
default_args = {
    'owner': 'arthur',
    'depends_on_past': False,
    'email': ['airflow@example.com'],
    'email_on_failure': False,
    'email_on_retry': False,
    'retries': 1,
    'retry_delay': timedelta(minutes=5),
    'queue': 'bash_queue',
    'pool': 'backfill',
    'priority_weight': 10,
    'end_date': datetime(2016, 1, 1),
    'wait_for_downstream': False,    
    'sla': timedelta(hours=2),
    'execution_timeout': timedelta(seconds=300),
    'on_failure_callback': some_function,
    'on_success_callback': some_other_function,
    'on_retry_callback': another_function,
    'sla_miss_callback': yet_another_function,
    'trigger_rule': 'all_success'
}
```
---

**Keys explanation:**
> **`owner`** (String): who owns this DAG, the name will appear in the list of dags web page

> **`depends_on_past`** (Boolean): It is for to check whether to run a task or not depending of its previous DAG run(last run).

> **`email`** (Array): List of email address to send if success

> **`email_on_failure`** (Boolean): If failed any task send a notification by email.

> **`email_on_retry`** (Boolean): If occurs retrying any task, send a notification by email.

> **`retries`** (Int): The number of retry if any task in DAG is failed

> **`retry_delay`** (timedelta Obj.): The interval between retries

> **`queue`**: Scheduler sent task to executor to run on the queue.

> **`pool`**: it can be used to **`limit the execution parallelism`** on arbitrary sets of tasks

> **`priority_weight`** (Int): The priority of the editing DAG

> **`end_date`** (datetime Obj.): The deadline of the task

> **`wait_for_downstream`** (Boolean): if you set **`True`** The task instances directly upstream from the task need to be in a **`sucess`** state.

> **`sla`** (timedelta Obj): Servuce Level Agreements(SLA), or time by which a task or DAG should have succeeded, can be set at a task level as a **`timedelta`** If one or many instances have not succeeded by that time, an alert email is sent detailing the list of tasks that missed their SLA.

> **`execution_timeout`** (timedelta Obj.): Max time allowed for the execution of this task instance, if it goes beyond it will raise and fail.

> **`on_failure_callback`**(callable):  A function to be called when a task instance of this task fails. a context dictionary is passed as a single parameter to this function. Context contains references to related objects to the task instance and is documented under the macros section of the API.

> **`on_success_callback`**(callable): much like the `on_failure_callback` except that it is executed when success occur.

> **`on_retry_callback`**(callable): much like the `on_failure_callback`except that it is executed when retries occur.

> **`sla_miss_callback`**(callable)

> **`trigger_rule`**(String): All operators have a `trigger_rule` argument which defines the rule by which the generated task get triggered. The default value for `trigger_rule` is `all_successand` can be defined as "trigger this task when all directly upstream tasks have succeeded". All other rules described here are based on direct parent tasks and are values that can be passed to any operator while creating tasks:

---

### Step 3. Create a DAG Object
```python
dag = DAG(
    dag_id='tutorial',
    default_args=default_args,
    description='A simple tutorial DAG',
    schedule_interval=timedelta(days=1),
    start_date=days_ago(2),
    tags=['example'],
)
```
---

**Keys explanation:**
> **dag_id** (String): set up your dag id which will appear in web page of DAGs.

> **default_args** (Dictionary): The dictionary we just define in previous step.

> **description** (String): description of this DAG

> **schedule_interval** (timedelta or String): the scheduler interval here, there are two main options to set up. I will highly recommand to use the following option [here](https://crontab.guru/)

> **start_date** (datetime obj.): Set up the initial/starting date.

> ***tags*** (Array): List of tags which will also show in web page of DAGs.


---

