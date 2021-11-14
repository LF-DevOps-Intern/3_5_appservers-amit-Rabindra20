 1. Create Django starter project in a separate virtual environment.
 2. Deploy the 3 instance of application using Gunicorn in 8089 port.
 3. Dump access log in a file in non-default pattern.
 4. Dump error log in a file.
 steps:<br/>
    <pre>-sudo apt install -y python3-venv<br/>
 virtual environment for django<br/>
    <pre>-python3 -m venv django_env<br/>
         -source django_env/bin/activate <br/>
    ![virtualenv](https://user-images.githubusercontent.com/53372486/141655880-63267d54-c25c-4dd8-89b4-95bd3b139385.png) <br/>

 install gunicorn<br/>
    <pre>-sudo apt install python3-django<br/>
    <pre>-pip install gunicorn<br/>
 create django-demo project<br/>
    <pre>-django-admin startproject demo<br/>
    <pre>nano demo/demo/settings.py<br/>
 added host ip in settings.py<br/>
    <pre>-ALLOWED_HOSTS = ['192.168.141.128'] 
    or <br/>
    keep bank for localhost
    <pre>-ALLOWED_HOSTS =[]
    <br/>
    <pre>mkdir conf<br/>
    <pre>nano gunicorn_config.py<br/>
# Deploy the 3 instance of application using Gunicorn in 8089 port.
added these lines in gunicorn_config.py<br/>
    command ='/home/rabindra/django_env/bin/gunicorn'<br/>
    pythonpath = '/home/rabindra/demo'<br/>
    bind = '192.168.141.128:8089' OR 'localhost:8089<br/>
    workers = 3<br/>
   ![port8089](https://user-images.githubusercontent.com/53372486/141655924-7e2255bc-61a6-4662-a70a-93a3dd1bea3c.png)<br/>

start gunicorn<br/>
    <pre>gunicorn -c conf/gunicorn_config.py demo.wsgi<br/>
 ![gunicornstart](https://user-images.githubusercontent.com/53372486/141655901-7184a3fa-7df2-4e04-9e93-48dcad527086.png)<br/>
 ![web](https://user-images.githubusercontent.com/53372486/141655898-f7ee9169-ebb5-4dd8-9d59-fcb4d73ce8cd.png)<br/>

# For access log and error log
<pre>gunicorn app_py:demo --error-logfile gunicorn.error.log --access-logfile gunicorn.log --capture-output<br/>