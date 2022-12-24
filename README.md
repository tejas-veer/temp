# setup

## Create Virtual Enviroment

## Install python 2.7.11
Download & Install
> https://www.python.org/downloads/release/python-2711/

Upgrade pip version
> pip install --upgrade pip==18.0.0


## Install Dependencies
 Install dependencies from requirement.txt 
> *pip install -r requirements.txt*

Install cryptography separately
> *pip install cryptography*

Some packages has to install manaually
```
socialweaverDB==1.0.0 
MySQL-python==1.2.5
```
> pip install file_name.whl


## Setup MySQL
#### Download
> https://dev.mysql.com/get/Downloads/MySQLInstaller/mysql-installer-community-8.0.30.0.msi

#### Install 
Select Custom and Install
> MySQL Workbench
> MySQL Server

Create Database
> socialweaver

Import dump File
1. Click **Data import/restore** from MANAGEMENT  
2. Select **Import from dump folder project**
3. Select dump file  
4. Click **Load Folder Contents** 
5. Select *socialweaver* Schema 
6. Uncheck *django_migrations* Schema Object
7. Go to **Import Progress** tab
8. Click **start import** 

## Setup SocialweaverDB
Clone repository 
> https://github.com/MyKinderPass/socialweaverDB

Change database configurations in *settings.py*
```
DATABASES = {
        'default': {
            'ENGINE': 'django.db.backends.mysql',
            'NAME': 'socialweaver',
            'USER': 'your_user',
            'PASSWORD': 'your_password',
            'OPTIONS': {'charset': 'utf8mb4', 'use_unicode': True,},
        }
}
```
    
Run this command 
> set  DJANGO_SETTINGS_MODULE=socialweaverDB.settings
> set APP_ENV=

 Change  models.py 
 *From*
```
 CharField(max_length=20480,
```
*To*
```
TextField(
```
Delete migration folder and Create Tables in DB 

> python manage.py makemigrations v1
> python manage.py migrate

Command to let api use Models
> python setup.py install

## Setup Socialweaver API
Clone repository 
> https://github.com/MyKinderPass/socialweaver-apis-v2

Run this command 
> set  DJANGO_SETTINGS_MODULE=socialweaverDB.settings
> set APP_ENV=

Start API using
> python wsgi.py
	 
