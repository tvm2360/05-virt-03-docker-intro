Задача 1
-
[https://hub.docker.com/tvm2360/custom-nginx/general ](https://hub.docker.com/repository/docker/tvm2360/custom-nginx/general)

Задача 2
-
[Console - command list](2024-12-12_11-06-15.png)

Задача 3
-
[Console - docker attach](2024-12-12_11-21-26.png)

После подключения к потоку ввода/вывода контейнера, нажатием комбинации клавиш Ctrl+C формируется управляющий сигнал SIGINT,
поэтому остановка контейнера в этом случае - предсказуемая реакция. 

[Console - docker exec](2024-12-12_11-45-25.png) [Console - ss](2024-12-12_11-50-08.png)

При запуске контейнера использовалась связь внешнего порта 8080 со внутренним контейнера 80 (-p 127.0.0.1:8080:80).
После изменения порта для прослушивания nginx на 81, вышеуказанная связь прервалась. Проброс порта 8080 на 80 продолжает
происходить, но внутри контейнера порт 80 ничем не обрабатывается.

Решение - поменять порт привязки со стороны контейнера на 81:

docker run -d -p 127.0.0.1:8080:81 -it --name custom-nginx-t2 --rm tvm2360/custom-nginx:1.0.0

Задача 4
-

[Console](2024-12-12_12-34-29.png)

