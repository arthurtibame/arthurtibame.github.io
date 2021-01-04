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
    weight: 10
---

## What is Airflow ?
> [**Airflow**](https://airflow.apache.org/) is an open-source workflow management platform written in [Python](https://www.python.org/)

## Requirements
- Python3
- Any operating system (Linux, Windows, MacOS)

--- 
### Step 1. Preparation
Here I will take Ubuntu for an example. First of all, I will highly recommand you to use virtualenv (venv)
```cmd
sudo apt update && \
 sudo apt install -y python3-venv 
```
  
  
---
### Step 2. Create Python Environment
Secondly create a folder airflow and create your env 
```cmd
$ mkdir $HOME/airflow
 $ cd $HOME/airflow
 $ python3 -m venv env
 $ source env/bin/activate
 
 # update pip 
 (env)$ pip3 install -U pip
```
  
  
---
### Step 3. Install apache-airflow
After install airflow by pip, try to type airflow and all configurations will appear in the folder
```cmd
(env)$ pip install apache-airflow

 (env)$ airflow
```
  

Your folder will involve files as follows:
```cmd
├── airflow.cfg
 ├── env
 ├── logs
 ├── unittests.cfg
 └── webserver_config.py
```
  
  
---
### Step 4. Initialize db and Create web user(default: sqlite)
airflow.db (sqlite file) will be create after enter the following command
```cmd
$ airflow db init
```
  

after sucessfully initialize database, we can start creating our admin user for airflow webserver
```cmd
$ airflow users create \
      --username admin \
      --firstname FIRST_NAME \
      --lastname LAST_NAME \
      --role Admin \
      --email admin@example.org
```
  
  
---
### Step 5. Start webserver and scheduler
Open two new command line terminals
```cmd
$ airflow webserver
```
   

```cmd
$ airflow scheduler
```
  
  
---  
### Step 6. Enter your Airflow website
Open your broswer and Enter URL: [localhost:8080](localhost:8080)

![](/posts/data_engineer/airflow/installation/result.png)