# Product Importer for ACME
This is the code repository for ACME Product Importer REST API. This allows a user to do bulk upload of products(about half a million) into a database without a frontend timeout.
It is made possible as a result of celery which is an asynchronous task queue based on distributed message passing. Task queues are used as a strategy to distribute the workload between threads/machines. In the link below is the API documentation:

https://documenter.getpostman.com/view/8255827/UVXbtz4k

### Setup
1. Clone this repository
2. Initialize gitflow in this repository (Learn more about gitflow in the gitflow section)
```bash
git flow init
```
Accept all defaults but set `Version tag prefix?` to "v"

### Creating branches
Create branches with git flow. See the following examples on how to create branches for features or hotfixes:  
```bash
git flow feature start feature-name # to work on a feature addition
git flow hotfix start bug-resolution-name # to work on a hotfix/bug fix
```

## Launching the API

### Setting up a virtual environment
```bash
sudo pip install virtualenv # Install the virtual environment.
sudo pip install -r requirements.txt # Install modules from requirements.txt
```

### Installing RabbitMQ

**Debian linux**
```bash
#!bin/bash
apt-get install -y erlang
apt-get install rabbitmq-server
```
**Mac**
```bash
#!bin/bash
brew install rabbitmq
vim ~/.bash_profile
export PATH=$PATH:/usr/local/sbin # Add it to the bottom of the file
```

### Starting RabbitMQ service

```bash
systemctl enable rabbitmq-server
systemctl start rabbitmq-server
systemctl status rabbitmq-server
```

### Starting The Worker Process

```bash
celery -A product_importer worker -l info
```

### Run application locally
```bash
# post installation of modules from requirements.txt
cd product_importer
python manage.py migrate # This will run all database migrations
python manage.py runserver # This will run the local server by default on port 8000
```

### Running Tests
Run this command to run tests:
```bash
pytest workflow/tests.py
```
