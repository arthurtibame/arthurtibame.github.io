---
title: "Airflow Installation"
date: 2021-01-04T08:21:25+08:00
hero: /posts/data_engineer/airflow/installation/airflow.svg
description: Installation of airflow
menu:
  sidebar:
    name: Installation
    identifier: airflow-installation
    parent: airflow
    weight: 9
---

## What is Airflow ?
> [**Airflow**](https://airflow.apache.org/) is an open-source workflow management platform written in [Python](https://www.python.org/)

</br>

## Requirements
- Python3
- Any operating system (Linux, Windows, MacOS)

</br>
</br>
--- 

### Step 1. Preparation
Here I will take Ubuntu for an example. First of all, I will highly recommand you to use virtualenv (venv)
```shell
sudo apt update && \
sudo apt install -y python3-venv 
```
</br>
</br> 

---
### Step 2. Create Python Environment
Secondly create a folder airflow and create your env 
```shell
$ mkdir $HOME/airflow
$ cd $HOME/airflow
$ python3 -m venv env
$ source env/bin/activate

# update pip 
(env)$ pip3 install -U pip
```
</br>
</br>  
  
---
### Step 3. Install apache-airflow
After install airflow by pip, try to type airflow and all configurations will appear in the folder
```shell
(env)$ pip install apache-airflow

(env)$ airflow
```
</br>
</br>  

Your folder will involve files as follows:
```shell
$ tree
├── airflow.cfg
├── env
├── logs
├── unittests.cfg
└── webserver_config.py
```

</br>
</br> 
  
---
### Step 4. Initialize db and Create web user(default: sqlite)
airflow.db (sqlite file) will be created after enter the following command
```shell
$ airflow db init
```

</br>
</br>

after sucessfully initialize database, we can start creating our admin user for airflow webserver
```shell
$ airflow users create \
      --username admin \
      --firstname FIRST_NAME \
      --lastname LAST_NAME \
      --role Admin \
      --email admin@example.org
```
</br>
</br>  

---
### Step 5. Start webserver and scheduler
Open two new command line terminals
```shell
$ airflow webserver
```
</br>
 
```shell
$ airflow scheduler
```
</br>

---  
### Step 6. Enter your Airflow website
Open your broswer and Enter URL: [localhost:8080](localhost:8080)

![](/posts/data_engineer/airflow/installation/result.png)

### Optional 1. Turn off official examples
[line 98](https://github.com/arthurtibame/airflow-tutorial/blob/main/airflow.cfg)

>> ~~load_examples = True~~ \

>> load_examples = False

### Optional 2. Change type of database
[line 29](https://github.com/arthurtibame/airflow-tutorial/blob/main/airflow.cfg)

>> ~~sql_alchemy_conn = sqlite:////home/arthur/airflow/airflow.db~~ \
  
>> sql_alchemy_conn = postgresql+psycopg2://USERNAME:PASSWORD@IP_ADDRESS:PORT/DATABASE

After changing the config, you should install required pip libraries and **reinitialize database as well as creating user for airflow webserver** in Step 5.
```shell
(env)$ pip install apache-airflow[postgresql]
```

## Reference 
To get more useful information related to the configuation
please check the official website [here](https://airflow.apache.org/docs/apache-airflow/stable/howto/index.html)



