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

Перед выполнением команды git clone https://github.com/skl256/grafana_stack_for_docker.git нужно установить git командой sudo dnf install git-core. 

![image](https://github.com/user-attachments/assets/5be48d5c-deff-4200-b269-7ec6a4f3b726)

После успешной установки git можно выполнить команду git clone https://github.com/skl256/grafana_stack_for_docker.git. При выполнении данной команды, Git создаст новую папку с именем репозитория (в данном случае `grafana_stack_for_docker`) в текущем каталоге, и скопирует все файлы и историю из удалённого репозитория в эту папку.

![image](https://github.com/user-attachments/assets/5ba1c456-f22f-40e0-83ad-b2d315875086)

Далее выполняем команду cd grafana_stack_for_docker, с ее помощью мы переходим в директорию grafana_stack_for_docker.

![image](https://github.com/user-attachments/assets/86b1df2a-c4d5-4de0-8847-bb68587a9ec5)

После этого можно из директории grafana_stack_for_docker выполнять команду sudo mkdir -p /mnt/common_volume/swarm/grafana/config. В результате выполнения этой команды будет создан каталог `/mnt/common_volume/swarm/grafana/config`, даже если родительские каталоги (`/mnt/common_volume/swarm/grafana`) отсутствуют. Если каталог уже существует, команда не вызовет ошибку и просто завершится успешно.

![image](https://github.com/user-attachments/assets/c757bda5-12ce-40f3-84bc-ab82cfb06000)

Далее нужно с помощью команды sudo mkdir -p /mnt/common_volume/grafana/{grafana-config,grafana-data,prometheus-data} создать новую директорию.

![image](https://github.com/user-attachments/assets/c9431c80-58f2-4437-8598-ee9e5a52f67d)

После создания новой директории уже можно выполнить команду sudo chown -R $(id -u):$(id -g) {/mnt/common_volume/swarm/grafana/config,/mnt/common_volume/grafana}, благодаря которой  владельцем и группой для всех файлов и поддиректорий в указанных директориях станут текущий пользователь и его группа. Это может быть полезно для обеспечения доступа к файлам для текущего пользователя, особенно в сценариях, где используются общие директории или контейнеры.

![image](https://github.com/user-attachments/assets/24c014ed-b4e3-4c94-88a7-1165861c560c)

После этого командой touch /mnt/common_volume/grafana/grafana-config/grafana.ini  создадим пустой файл с этим именем по указанному пути. Если файл уже существует, команда просто обновит время его последнего доступа и модификации, не изменяя его содержимое. 

![image](https://github.com/user-attachments/assets/90b45131-9b78-4fa2-b7da-86e90df841db)

Далее командой `cp config/* /mnt/common_volume/swarm/grafana/config/` копируем все файлы из директории `config` в директорию `/mnt/common_volume/swarm/grafana/config/`. Если в целевой директории уже существуют файлы с такими же именами, данной командой они будут перезаписаны без предупреждения (если не указаны дополнительные параметры, такие как `-i` для интерактивного режима, который запрашивает подтверждение перед перезаписью). 

![image](https://github.com/user-attachments/assets/a86b05d2-94aa-43c2-8091-0f4c7e1f1a00)

Далее выполняем команду sudo mv grafana.yaml docker-compose.yaml. Данная команда переименовывает файл `grafana.yaml` в `docker-compose.yaml`. Если файл `docker-compose.yaml` уже существует, он будет перезаписан без предупреждения.

![image](https://github.com/user-attachments/assets/d4f0d07c-a775-425a-8366-f306f06c1d42)

После этого запускаем команду `sudo docker compose up -d`, которая запускает контейнеры, определенные в файле `docker-compose.yml`, с правами суперпользователя и в фоновом режиме.

![image](https://github.com/user-attachments/assets/828f7622-d9a1-492c-8358-6c329297219b)
