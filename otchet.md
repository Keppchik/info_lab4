# Лабораторная работа 4

1. Создаем файл Dockerfile и записываем в него следующее для установки aafire и ping:
```bash
FROM ubuntu:latest

RUN apt-get update && apt-get install -y libaa-bin
RUN apt-get install -y iputils-ping
```
2. Cоздаем 2 образа из Dockerfile и называем их mycontainer1 и mycontainer2 c помощью команд:
```bash
docker build -t mycontainer1 .
```
3. Запускаем контейнер и проверяем работу приложения aafire:
```bash
docker run -it mycontainer1
```
```bash
aafire
```
<img width="975" alt="Screenshot 2024-12-02 at 21 47 03" src="https://github.com/user-attachments/assets/99dd18e6-94db-4ecd-bc4f-eb5014c14d89">

4. Создадим собственную сеть:
```bash
docker network create myNetwork
```
5. Подключаем наши контейнеры к созданной сети:
```bash
docker network connect myNetwork mycontainer1
```
6. Смотрим настройки нашей сети командой:
```bash
docker network inspect myNetwork
```
<img width="1008" alt="Screenshot 2024-12-02 at 21 51 52" src="https://github.com/user-attachments/assets/6eecb7c9-4cc9-4237-b4f1-27b9a4d59b57">

7. Проверим соединение между двумя нашими контейнерами с помощью следующей команды:
```bash
docker exec -it mycontainer1 ping -c4 mycontainer2
```
<img width="1008" alt="Screenshot 2024-12-02 at 21 53 13" src="https://github.com/user-attachments/assets/e97280fe-88e7-4394-942b-34f87b596c54">
