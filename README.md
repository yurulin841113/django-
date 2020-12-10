# My Django環境


## :memo: Where do I start?

### 安裝環境
Win ---> python -m venv (取名字)
Linux ---> python -m venv (取名字)

>(佈署網站) 
>virtualenv --python=python3.5 djangogirls_venv


### 切換環境

Win ----> (名字)\Scripts\activate
Linux ----> source (名字)/bin/activate



### 安裝版本(最新3.1.4)

pip install Django==3.1.4
python -m pip install --user --upgrade pip
>確認安裝 python -> import django -> django.VERSION


### 建立專案

django-admin.py startproject (取名字)

### 進入專案 & 建立webapp

cd (專案名字)

python manage.py startapp (取webapp名字)

### 建立tempaltes & 更改tepmlates位置
mkdir templates ->更改setting.py加上'DIRS': [os.path.join(BASE_DIR, 'templates')],

### 建立static 

mkdir static ->更改setting.py加上STATIC_DIRS =[os.path.join(BASE_DIR, 'static')]

>(佈署網站記得加!)
STATIC_ROOT = "/home/yurulin841113/mainsite/static"
STATIC_ROOT = os.path.join(BASE_DIR, "static")

### 創造Admin
python manage.py createsuperuser

### 安裝markdown語法(佈署網站記得加!)
pip install django-markdown-deux

pip freeze > requirements.txt



### 佈署網站_PythonAnywhere_com_wsgi.py
import os
import sys

path = '/home/<your-PythonAnywhere-username>/mysite'  # use your own PythonAnywhere username here
if path not in sys.path:
    sys.path.append(path)

os.environ['DJANGO_SETTINGS_MODULE'] = 'mysite.settings'

from django.core.wsgi import get_wsgi_application
from django.contrib.staticfiles.handlers import StaticFilesHandler
application = StaticFilesHandler(get_wsgi_application())
