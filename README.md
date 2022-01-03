# Product Importer for ACME
This is the code repository for ACME Product Importer REST API

### Setup
1. Clone this repository
2. Initialize gitflow in this repository (Learn more about gitflow in the gitflow section)
```bash
git flow init
```
Accept all defaults but set `Version tag prefix?` to "v"

### Creating branches
Create branches with git flow. See the following examples on how to create branches for features or hotfixes:  
```
git flow feature start feature-name # to work on a feature addition
git flow hotfix start bug-resolution-name # to work on a hotfix/bug fix
```

## Launching the API

### Setting up a virtual environment
```bash
sudo pip install virtualenv # Install the virtual environment.
sudo pip install -r requirements.txt # Install modules from requirements.txt
```

### Run application locally
```bash
# post installation of modules from requirements.txt
cd product_import
python manage.py migrate # This will run all database migrations
python manage.py runserver # This will run the local server by default on port 8000
```

### Running Tests