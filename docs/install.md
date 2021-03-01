# Hujan.io

## Server Installation And Configuration

### Pre-Installation

You need to install the following dependencies :

- python3.6
- Nginx
- virtualenv

### Application Setup


Clone the latest source code from the repository, and I assume you put it to `/var/www/html/`

```
$ cd /var/www/html/
$ git clone {repository}
$ cd hujan_ui
```

#### With Virtuan Environment
Create virtualenv with python3

```
$ virtualenv --python=python3.6
$ source/env/bin/activate
$ pip install -r requirements.txt
$ pip install gunicorn
```

#### Without Virtual Environment
```
$ pip3.6 install -r requirements.txt
$ pip3.6 install gunicorn
```

Then create a configuration file, just copy from sample file and modify as your preference

```
$ cp hujan_ui/local_settings.sample.py hujan_ui/local_settings.py
```

Configure MAAS in `local_settings.py` with:
```
MAAS_API_KEY = ""
MAAS_URL = ""
``` 

Then run the database migration

```
$ python manage.py migrate
```

Then create first superuser

```
$ python manage.py createsuperuser
Username (leave blank to use 'root'):
Email address:
Password:
Password (again):
Superuser created successfully.
```

Then generate static files

```
$ python manage.py collectstatic
```

Create logs directory

```
$ mkdir logs
```

Runing the service

```
python manage.py runserver 8001
```

Then open your browser `http://[hujan-ip]:8001` and viola your web apps is already running !

### Run Hujan UI as Systemd Service 

To run `Hujan UI` as Systemd, simply you can follow this instruction.  

- Create `hujan_ui.service` file
```
# touch /etc/systemd/system/hujan_ui.service
```

- Add the following entry.
```
[Unit]
Description=hujan ui daemon
After=network.target

[Service]
User=root
Group=root
WorkingDirectory=/var/www/html/hujan-ui/

## with virtual environment
ExecStart=/var/www/html/hujan-ui/env/bin/python manage.py runserver 8001

## without virtual environment
#ExecStart=/usr/bin/python3.6 /var/www/html/hujan-ui/manage.py runserver 8001

[Install]
WantedBy=multi-user.target
```

- Reload daemon and start the service.

```
# systemctl daemon-reload
# systemctl start hujan_ui.service
```