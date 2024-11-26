## Лабораторная работа No4

1\. Установка Docker :

Сначала вам нужно установить Docker. Можно установить на виртуальную машину Linux или с помощью WSL (подсистема Windows для Linux).

2\. Создать Dockerfile :

- Создайте новый каталог для своего проекта, а затем создайте в нем файл Dockerfile :

```bash
mkdir docker-aafire
cd docker-aafire
touch Dockerfile
nano Dockerfile
```

Содержимое Dockerfile:

```bash
FROM ubuntu:24.04
RUN apt-get update && apt-get install -y libaa-bin
CMD ["aafire"]
RUN apt-get update && apt-get install -y iputils-ping 
```

3\. Создайте образ Docker :

- Откройте терминал и выполните следующую команду, чтобы создать образ из Dockerfile:

```bash
docker build -t aafire-image .
```

![image](https://github.com/haha523/lab_4.linux/blob/043c707c9ec97f0c132255c5fdb938dc280bc506/png%20for%20lab/X%C3%A2y%20d%E1%BB%B1ng%20l%E1%BA%A1i%20Docker%20image%201.png)


4\. Запускайте контейнеры с помощью aafire :

Запустите контейнер из вновь созданного образа:

```bash
docker run -d --name aafire-container1 aafire-image
```

![image](https://github.com/haha523/lab_4.linux/blob/043c707c9ec97f0c132255c5fdb938dc280bc506/png%20for%20lab/containners%201.png)

```bash
docker run -d --name aafire-container2 aafire-image
```

![image](https://github.com/haha523/lab_4.linux/blob/043c707c9ec97f0c132255c5fdb938dc280bc506/png%20for%20lab/containners%202.png)


5\. Создать сеть Docker:

Создайте новую сеть для контейнеров:

```bash
docker network create myNetwork
```

![image](https://github.com/haha523/lab_4.linux/blob/c222540dd54b96d47e4cfe9d445459df2506376e/png%20for%20lab/docker%20network%20connect%20myNetwork.png)

6\. Подключение контейнеров к сети:

Подключите контейнеры к вновь созданной сети:

```bash
docker network connect myNetwork aafire-container1
```

```bash
docker network connect myNetwork aafire-container2
```

![image](https://github.com/haha523/lab_4.linux/blob/c222540dd54b96d47e4cfe9d445459df2506376e/png%20for%20lab/k%E1%BA%BFt%20n%E1%BB%91i%20t%E1%BB%ABng%20container%20v%E1%BB%9Bi%20m%E1%BA%A1ng.png)


7\. Проверить сеть :

Проверьте конфигурацию сети:

```bash
docker network inspect myNetwork
```

![image](https://github.com/haha523/lab_4.linux/blob/c222540dd54b96d47e4cfe9d445459df2506376e/png%20for%20lab/B%C6%B0%E1%BB%9Bc%207%20Ki%E1%BB%83m%20Tra%20C%E1%BA%A5u%20H%C3%ACnh%20M%E1%BA%A1ng.png)

8\. Проверьте соединение между контейнерами:

- Используйте ping для проверки соединения между двумя контейнерами. Для начала вам нужно зайти в один из контейнеров:

```bash
docker exec -it aafire-container1 bash
```

- В оболочке контейнера вы можете пропинговать оставшийся контейнер:

```bash
ping aafire-container2
```

Результат :

![image](https://github.com/haha523/lab_4.linux/blob/c222540dd54b96d47e4cfe9d445459df2506376e/png%20for%20lab/l%E1%BB%ADa%201.png)


Краткое содержание :

⦁  Установите Докер.

⦁  Создайте Dockerfile для установки aafire и ping.

⦁  Создайте образ и запустите два контейнера.

⦁  Создавайте сети и соединяйте контейнеры.

⦁  Проверьте соединение между контейнерами.



























