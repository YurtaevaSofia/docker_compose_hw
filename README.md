# Задача 1

Собран кастомный образ nginx на основе `nginx:1.29.0` с заменённой индекс-страницей (`Dockerfile`, `index.html`), собран и запушен в Docker Hub с тегом `1.0.0`.

Ответ: https://hub.docker.com/r/yurtaevasofia/custom-nginx

# Задача 2

<img width="1084" height="344" alt="Screenshot 2026-08-21 at 18 58 10" src="https://github.com/user-attachments/assets/b252a97e-f1a6-4bf2-bb0c-16e4fb5b5dda" />


# Задача 3

<img width="1086" height="459" alt="Screenshot 2026-08-21 at 20 28 59" src="https://github.com/user-attachments/assets/e431059b-8072-45a3-bcd8-47f32948ed40" />

 attach подключил терминал напрямую к stdin/stdout контейнера, Ctrl-C отправил сигнал прерывания главному процессу
  (nginx), тот завершился — а поскольку в докере жизненный цикл контейнера привязан к процессу с PID 1, контейнер
  тоже остановился.

<img width="438" height="307" alt="Screenshot 2026-08-21 at 20 32 33" src="https://github.com/user-attachments/assets/99f64069-465f-40bb-b64b-f4928238d45d" />

проброс порта (-p 127.0.0.1:8080:80) — это статическое правило NAT, созданное при 
  старте контейнера для конкретной пары хост-порт → порт-контейнера-80. Мы поменяли порт, на котором nginx слушает
  внутри контейнера, на 81, но правило проброса как слушало 80→8080, так и слушает — а на 80-м порту внутри
  контейнера теперь никто не слушает. Поэтому curl http://127.0.0.1:8080 снаружи получит connection refused/empty
  reply, хотя docker port по-прежнему покажет старый маппинг 80→8080.

  <img width="548" height="99" alt="Screenshot 2026-08-21 at 20 35 59" src="https://github.com/user-attachments/assets/e12d7b95-772b-4c66-99d1-ebc5d616db3d" />


# Задача 4

<img width="696" height="399" alt="Screenshot 2026-08-23 at 09 50 36" src="https://github.com/user-attachments/assets/897c6384-6f25-4122-9154-ea43858324ce" />

# Задача 5

<img width="796" height="372" alt="Screenshot 2026-08-23 at 10 23 29" src="https://github.com/user-attachments/assets/3df1236b-4034-4247-a318-8112ae3def26" />

<img width="890" height="755" alt="Screenshot 2026-08-23 at 10 35 53" src="https://github.com/user-attachments/assets/d17cb7bd-9f73-48d5-85d2-3620ebda5ea4" />
<img width="1680" height="1050" alt="Screenshot 2026-08-23 at 10 30 03" src="https://github.com/user-attachments/assets/e9bcef64-79a2-4c77-af23-1412225273b3" />

<img width="902" height="469" alt="Screenshot 2026-08-23 at 10 36 03" src="https://github.com/user-attachments/assets/7021c3e0-69b8-43aa-bd64-13b31301a14b" />
<img width="761" height="297" alt="Screenshot 2026-08-23 at 10 38 29" src="https://github.com/user-attachments/assets/1eadb632-ca1c-437f-9894-8a5367cb805d" />

