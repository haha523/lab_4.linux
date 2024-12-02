## Лабораторная работа No4

Задание 1 :

1\. Создать папку проекта:
- Создайте новую папку для вашего проекта:

```bash
mkdir docker-cowsay
cd docker-cowsay
```
![image](https://github.com/haha523/lab_4.linux/blob/21975dc9072328ec80bc7ed17e62fdf9c352e279/png%20for%20lab/b%C3%A0i%201%20t%E1%BA%A1o%20b%C3%B2.png)


2\. Создать Docker-файл:

- Содержимое Dockerfile:

```bash
FROM ubuntu:latest
RUN apt-get update && apt-get install -y cowsay fortune
CMD ["/usr/games/cowsay", "Moo"]
```

3\. Создание образа Docker:
- Откройте терминал (или командную строку в Windows) и перейдите в папку, содержащую Dockerfile. Запустите следующую команду для создания образа:

```bash
docker build -t cowsay .
```

![image](https://github.com/haha523/lab_4.linux/blob/21975dc9072328ec80bc7ed17e62fdf9c352e279/png%20for%20lab/t%E1%BA%A1o%20b%C3%B2%20X%C3%A2y%20D%E1%BB%B1ng%20Docker%20Image.png)

4\. Результат :

```bash
docker run cowsay
```

![image](https://github.com/haha523/lab_4.linux/blob/21975dc9072328ec80bc7ed17e62fdf9c352e279/png%20for%20lab/h%C3%ACnh%20%E1%BA%A3nh%20con%20b%C3%B2.png)


Задание 2 :

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
FROM ubuntu:latest
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

```bash
docker run -it aafire-image
```

![image](https://github.com/haha523/lab_4.linux/blob/fd771498b493c5c0bd2909dc72e9ee9cf770882d/png%20for%20lab/h%C3%ACnh%20%E1%BA%A3nh%20l%E1%BB%ADa%202.png)


Краткое содержание :

⦁  Установите Докер.

⦁  Создайте Dockerfile для установки aafire и ping.

⦁  Создайте образ и запустите два контейнера.

⦁  Создавайте сети и соединяйте контейнеры.

⦁  Проверьте соединение между контейнерами.



























