# etmanov_d_e
Устанавливаем утилиту WGET командой sudo yum install wget

![image](https://github.com/user-attachments/assets/8b4c434f-9e1a-4300-92c2-ca4200cc9a17)

Получаем ошибку. Чтобы ее решить переходим в браузер, вставляем ошибку в поисковую строку и переходим на Stackoverflow. Там находим решение данной проблемы.
Для решения проблемы нужно в командной строке ввести команду su root и ввести пароль

![image](https://github.com/user-attachments/assets/0b21be17-8449-4526-9637-752d4c16e244)

Далее нужно ввести команду vi /etc/sudoers

![image](https://github.com/user-attachments/assets/e7d958ec-e413-4aa7-93dc-bc3e156d912f)

В открывшемся файле нужно найти строку, которая начинается с root, затем скопировать эту строку и вставить ее на следующей строке, заменив root на имя пользователя

![image](https://github.com/user-attachments/assets/c5f869fc-aba5-4e40-ac94-d197b5d8abd2)

После этого нужно нажать Esc -> Shift + ж -> ввести wq! -> Enter. После этого ошибка будет решена! Проверить это можно повторным вводом команды sudo yum install wget

![image](https://github.com/user-attachments/assets/509a3deb-80d0-411d-b13f-1763c88bad72)

Вводим команду sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo

![image](https://github.com/user-attachments/assets/92a74181-cef0-4599-8c3b-770478a2dc13)

Вводим команду sudo yum install docker-ce docker-ce-cli containerd.io

![image](https://github.com/user-attachments/assets/807a967c-d370-45c8-b9d0-f8002eb7dd2f)

![image](https://github.com/user-attachments/assets/75a62500-ebfc-4fa1-a61f-8741b52d9c91)

Вводим команду sudo systemctl enable docker --now

![image](https://github.com/user-attachments/assets/279816af-cb0e-41f6-8503-e790aa0d8737)

Вводим команду COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4). Она определяет и сохраняет в переменную `COMVER` номер последней версии `docker-compose` из репозитория GitHub

![image](https://github.com/user-attachments/assets/ccbb4fb0-3ab9-4848-a1c3-b52339e7ac6c)

Далее вводим команду sudo curl -L "https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose. Данная команда загружает последнюю версию `docker-compose` для вашей операционной системы и архитектуры и сохраняет ее в `/usr/bin/docker-compose`, что позволяет использовать `docker-compose` как обычную команду в терминале.

![image](https://github.com/user-attachments/assets/784b4d0f-b8ee-4d1b-bd3b-e0f203badaec)

Далее нужно ввести команды sudo chmod +x /usr/bin/docker-compose и docker-compose --version, после чего мы увидим версию Docker Compose. Чтобы убедиться, что все выполнено правильно, нужно перейти по ссылке https://api.github.com/repos/docker/compose/releases/latest, после чего нажать Ctrl + f и в поисковой строке вбить tag_name. Значение данной переменной должно совпадать со значением из командной строки.

![image](https://github.com/user-attachments/assets/8c6df155-e5c4-4314-9882-0b7aa24d6336)

![image](https://github.com/user-attachments/assets/6a3489da-2a18-4f83-a972-520199bcc0aa)


