Rabbitmq Васёв А.В.

Задание 1. Установка RabbitMQ

Используя Vagrant или VirtualBox, создайте виртуальную машину и установите RabbitMQ. Добавьте management plug-in и зайдите в веб-интерфейс.

![alt text](https://github.com/rus42/rabbitmq/blob/main/Task_1.png)

Задание 2. Отправка и получение сообщений

Используя приложенные скрипты, проведите тестовую отправку и получение сообщения. Для отправки сообщений необходимо запустить скрипт producer.py.

Для работы скриптов вам необходимо установить Python версии 3 и библиотеку Pika. Также в скриптах нужно указать IP-адрес машины, на которой запущен RabbitMQ, заменив localhost на нужный IP.

$ pip install pika

Зайдите в веб-интерфейс, найдите очередь под названием hello и сделайте скриншот. После чего запустите второй скрипт consumer.py и сделайте скриншот результата выполнения скрипта

![alt text](https://github.com/rus42/rabbitmq/blob/main/Task_2.1.png)

![alt text](https://github.com/rus42/rabbitmq/blob/main/Task_2.2.png)

Задание 3. Подготовка HA кластера

Используя Vagrant или VirtualBox, создайте вторую виртуальную машину и установите RabbitMQ. Добавьте в файл hosts название и IP-адрес каждой машины, чтобы машины могли видеть друг друга по имени.

Пример содержимого hosts файла:

$ cat /etc/hosts
192.168.0.10 rmq01
192.168.0.11 rmq02

После этого ваши машины могут пинговаться по имени.

Затем объедините две машины в кластер и создайте политику ha-all на все очереди.

![alt text](https://github.com/rus42/rabbitmq/blob/main/Task_3.1.png)

![alt text](https://github.com/rus42/rabbitmq/blob/main/Task_3.2.png)

$ rabbitmqctl cluster_status

![alt text](https://github.com/rus42/rabbitmq/blob/main/Task_3.3.png)

![alt text](https://github.com/rus42/rabbitmq/blob/main/Task_3.4.png)

Для закрепления материала снова запустите скрипт producer.py и приложите скриншот выполнения команды на каждой из нод:

$ rabbitmqadmin get queue='hello'

![alt text](https://github.com/rus42/rabbitmq/blob/main/Task_3.5.png)

![alt text](https://github.com/rus42/rabbitmq/blob/main/Task_3.6.png)


После чего попробуйте отключить одну из нод, желательно ту, к которой подключались из скрипта, затем поправьте параметры подключения в скрипте consumer.py на вторую ноду и запустите его.

Приложите скриншот результата работы второго скрипта.

![alt text](https://github.com/rus42/rabbitmq/blob/main/Task_3.5.png)

![alt text](https://github.com/rus42/rabbitmq/blob/main/Task_3.6.png)

