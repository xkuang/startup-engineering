Регистрация аккаунта на Амазоне
-------------------------------

1. Зайдите на http://aws.amazon.com/, нажимайте Get Started for Free. Введите свои данные.

2. Откройте письмо на почте, из письма нажимаете ссылку Free Tier. Выбираете Amazon EC2 - Get Started For Free.

3. Введите данные кредитной карты. Не бойтесь, с вас возьмут не больше доллара в первый год пользования, если у вас в каждый
момент времени будет работать только один движок типа t1.micro.

2. [Пройдите туториал по терминалу линукса](https://d396qusza40orc.cloudfront.net/startup/lecture_slides%2Flecture3-linux-ssjs-v2.pdf), если вы не профи.

Подъём дев-сервера
------------------

1. Зайдите в AWS Management Console, поднимите инстанс t1.micro, сохраните ключ от него (файл с расширением `.cer`) и приконнектитесь
к нему по ssh:
    
        ssh -i ~/Downloads/privatekey.cer ubuntu@ec2-54-213-214-189.us-west-2.compute.amazonaws.com

2. Залейте Джанго-проект с вики-движком на битбакет. Создайте в настройках проекта Deployment key (ридонли-ключ для выкачивания вашего проекта
на продакшн-сервер), выкачайте на Амазоне простой проект. Поставьте на Амазоне средства установки питона и Джангу:

        sudo apt-get install python3-setuptools
        sudo easy_install3 pip 
        sudo easy_install3 virtualenv
        sudo pip install django

3. Стартуйте сервер разработчика на Амазоне:

        python3 manage.py runserver

Подъём продакшн-сервера
-----------------------

Дальше мы будем настраивать боевую конфигурацию сервера. Джанго будет запущен в связке nginx + uwsgi + Django, в качестве базы поднимем mysql.

1. Найдите на сайте nginx инструкции по его сборке, скачайте и соберите nginx на Амазоне.

2. Поставьте uwsgi через пакетный менеджер Убунты. Напишите конфиги nginx и uwsgi. [Пример uwsgi-конфига](uwsgi_example.conf).
    [Пример nginx-конфига](nginx_example.conf)

3. [Поставьте mysql, создайте базу.](http://developingable.com/install-mysql-with-django/)

4. Заставьте всё это работать.

Вопросы на семестр
------------------

0. Что такое logrotate?

1. Что такое vagrant?

2. Как и зачем деплоиться через deb-пакеты?

3. Что такое elasticsearch, zabbix, nagios, что из этого используют админы, как это поднять и чем это лучше ручного грепа по логам?

