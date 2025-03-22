# etmanov_d_e
__1. Установка утилиты WGET__

Устанавливаем утилиту WGET командой 

`sudo yum install wget`

![image](https://github.com/user-attachments/assets/8b4c434f-9e1a-4300-92c2-ca4200cc9a17)

Получаем ошибку. Чтобы ее решить переходим в браузер, вставляем ошибку в поисковую строку и переходим на Stackoverflow. Там находим решение данной проблемы.
Для решения проблемы нужно в командной строке ввести команду `su root` и ввести пароль. Данная команда позволит сменить пользователя на пользователя с именем "root".

![image](https://github.com/user-attachments/assets/0b21be17-8449-4526-9637-752d4c16e244)

Далее вводим команду 

`vi /etc/sudoers`,

которая позволяет администратору системы изменять настройки прав доступа для использования `sudo`

![image](https://github.com/user-attachments/assets/e7d958ec-e413-4aa7-93dc-bc3e156d912f)

В открывшемся файле нужно найти строку, которая начинается с `root`, затем скопировать эту строку и вставить ее на следующей строке, заменив root на имя пользователя.

![image](https://github.com/user-attachments/assets/c5f869fc-aba5-4e40-ac94-d197b5d8abd2)

После этого нужно нажать Esc -> Shift + : -> ввести wq! -> Enter, чтобы выйти из редактора vim с сохранением. После этого ошибка будет решена! Проверить это можно повторным вводом команды 

`sudo yum install wget`

![image](https://github.com/user-attachments/assets/509a3deb-80d0-411d-b13f-1763c88bad72)

__2. Установка и работа с Docker__

Вводим команду 

`sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo`,

в результате выполнения которой будет загружен файл `docker-ce.repo` из указанного URL и сохранён в директории `/etc/yum.repos.d/`, что позволит системе использовать этот репозиторий для установки и обновления пакетов Docker с помощью `yum`.

![image](https://github.com/user-attachments/assets/92a74181-cef0-4599-8c3b-770478a2dc13)

Теперь используем команду 

`sudo yum install docker-ce docker-ce-cli containerd.io`,

которая установит Docker и его необходимые компоненты, что позволит создавать и управлять контейнерами.

![image](https://github.com/user-attachments/assets/807a967c-d370-45c8-b9d0-f8002eb7dd2f)

![image](https://github.com/user-attachments/assets/75a62500-ebfc-4fa1-a61f-8741b52d9c91)

Вводим команду 

`sudo systemctl enable docker --now`,

которая выполняет сразу 2 функции: включает автозапуск Docker при загрузке ОС, а флаг `--now` запускает Docker сразу же, если он еще не работает.

![image](https://github.com/user-attachments/assets/279816af-cb0e-41f6-8503-e790aa0d8737)

Используем команду 

`COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)`

Она определяет и сохраняет в переменную `COMVER` номер последней версии `docker-compose` из репозитория GitHub

![image](https://github.com/user-attachments/assets/ccbb4fb0-3ab9-4848-a1c3-b52339e7ac6c)

Далее вводим команду 

`sudo curl -L "https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose`

Данная команда загружает последнюю версию `docker-compose` для вашей операционной системы и архитектуры и сохраняет ее в `/usr/bin/docker-compose`, что позволяет использовать `docker-compose` как обычную команду в терминале.

![image](https://github.com/user-attachments/assets/784b4d0f-b8ee-4d1b-bd3b-e0f203badaec)

Далее нужно ввести команды 

`sudo chmod +x /usr/bin/docker-compose` и `docker-compose --version`,

после чего мы увидим версию Docker Compose. Чтобы убедиться, что все выполнено правильно, нужно перейти по ссылке `https://api.github.com/repos/docker/compose/releases/latest`, после чего нажать `Ctrl + f` и в поисковой строке написать `tag_name`. Значение данной переменной должно совпадать со значением из командной строки.

![image](https://github.com/user-attachments/assets/8c6df155-e5c4-4314-9882-0b7aa24d6336)

![image](https://github.com/user-attachments/assets/6a3489da-2a18-4f83-a972-520199bcc0aa)

Перед выполнением команды 

`git clone https://github.com/skl256/grafana_stack_for_docker.git` 

нужно установить git командой 

`sudo dnf install git-core`


![image](https://github.com/user-attachments/assets/5be48d5c-deff-4200-b269-7ec6a4f3b726)

После успешной установки git можно выполнить команду 

`git clone https://github.com/skl256/grafana_stack_for_docker.git`

При выполнении данной команды, Git создаст новую папку с именем репозитория (в данном случае `grafana_stack_for_docker`) в текущем каталоге, и скопирует все файлы и историю из удалённого репозитория в эту папку.

![image](https://github.com/user-attachments/assets/5ba1c456-f22f-40e0-83ad-b2d315875086)

Далее выполняем команду 

`cd grafana_stack_for_docker`

с ее помощью мы переходим в директорию grafana_stack_for_docker.

![image](https://github.com/user-attachments/assets/86b1df2a-c4d5-4de0-8847-bb68587a9ec5)

После этого можно из директории `grafana_stack_for_docker` выполнять команду 

`sudo mkdir -p /mnt/common_volume/swarm/grafana/config`

В результате выполнения этой команды будет создан каталог `/mnt/common_volume/swarm/grafana/config`, даже если родительские каталоги (`/mnt/common_volume/swarm/grafana`) отсутствуют. Если каталог уже существует, команда не вызовет ошибку и просто завершится успешно.

![image](https://github.com/user-attachments/assets/c757bda5-12ce-40f3-84bc-ab82cfb06000)

Далее нужно создать новую директорию с помощью команды 

`sudo mkdir -p /mnt/common_volume/grafana/{grafana-config,grafana-data,prometheus-data}`

![image](https://github.com/user-attachments/assets/c9431c80-58f2-4437-8598-ee9e5a52f67d)

После создания новой директории выполняем команду 

`sudo chown -R $(id -u):$(id -g) {/mnt/common_volume/swarm/grafana/config,/mnt/common_volume/grafana}`,

благодаря которой  владельцем и группой для всех файлов и поддиректорий в указанных директориях станут текущий пользователь и его группа. Это может быть полезно для обеспечения доступа к файлам для текущего пользователя, особенно в сценариях, где используются общие директории или контейнеры.

![image](https://github.com/user-attachments/assets/24c014ed-b4e3-4c94-88a7-1165861c560c)

После этого командой 

`touch /mnt/common_volume/grafana/grafana-config/grafana.ini`

создадим пустой файл с этим именем по указанному пути. Если файл уже существует, команда просто обновит время его последнего доступа и модификации, не изменяя его содержимое. 

![image](https://github.com/user-attachments/assets/90b45131-9b78-4fa2-b7da-86e90df841db)

Далее командой 

`cp config/* /mnt/common_volume/swarm/grafana/config/`

копируем все файлы из директории `config` в директорию `/mnt/common_volume/swarm/grafana/config/`. Если в целевой директории уже существуют файлы с такими же именами, данной командой они будут перезаписаны без предупреждения (если не указаны дополнительные параметры, такие как `-i` для интерактивного режима, который запрашивает подтверждение перед перезаписью). 

![image](https://github.com/user-attachments/assets/a86b05d2-94aa-43c2-8091-0f4c7e1f1a00)

Далее выполняем команду 

`sudo mv grafana.yaml docker-compose.yaml`
Данная команда переименовывает файл `grafana.yaml` в `docker-compose.yaml`. Если файл `docker-compose.yaml` уже существует, он будет перезаписан без предупреждения.

![image](https://github.com/user-attachments/assets/d4f0d07c-a775-425a-8366-f306f06c1d42)

После этого выполняем команду 

`sudo docker compose up -d`,

которая запускает контейнеры, определенные в файле `docker-compose.yml`, с правами суперпользователя и в фоновом режиме.

![image](https://github.com/user-attachments/assets/828f7622-d9a1-492c-8358-6c329297219b)

__4 Пара__

Запускаем docker compose командой 

`sudo docker compose up -d`,

которая запускает контейнеры, определенные в файле `docker-compose.yml`, с правами суперпользователя и в фоновом режиме.
Флаг `-d` в команде `sudo docker compose up -d` означает, что Docker Compose должен запустить контейнеры в фоновом режиме (detached mode). Это позволяет вам продолжать использовать терминал для выполнения других команд, в то время как контейнеры работают в фоновом режиме.

Если не использовать флаг `-d`, команда `docker compose up` будет блокировать терминал, выводя логи контейнеров, и вы не сможете выполнять другие команды, пока не остановите выполнение этой команды (обычно с помощью `Ctrl+C`). 

![image](https://github.com/user-attachments/assets/35b45cb5-2776-4697-92b5-aa59d695a7bb)

Теперь используем команду для удаления контейнеров и остановки

`sudo docker compose down`,

которая используется для полной остановки и удаления всех ресурсов, связанных с проектом Docker Compose, что позволяет вернуть систему в начальное состояние.

![image](https://github.com/user-attachments/assets/90a033f1-305e-4670-9d2d-0df361b076ee)

Теперь нужно заново запустить docker-compose комадой 

`sudo docker compose up -d`

![image](https://github.com/user-attachments/assets/bb6abe49-c875-43e0-a2cc-5f3dd5ba2bbd)

После этого используем команду 

`sudo docker compose stop`,

которая используется для безопасной остановки всех контейнеров, определенных в Docker Compose, без их удаления.

![image](https://github.com/user-attachments/assets/a18dae54-7948-4f1b-82bd-a1bb9ab8ff17)

После очередного запуска docker-compose командой `sudo docker compose up -d` выполняем команду 

`sudo docker compose ps`,

которая позволяет быстро получить представление о состоянии всех контейнеров, которые определены в вашем файле `docker-compose.yml`, и узнать, какие из них активны в данный момент.

![image](https://github.com/user-attachments/assets/d0ff73c1-40e4-4daa-9aa3-f40c966226b7)

Используем команду 

`pwd`

Она выводит адрес текущего рабочего каталога

![image](https://github.com/user-attachments/assets/86d81208-6e36-487a-b505-7369e9ba93ec)


__5 пара__

Из найденного репозитория были скачаны файлы `docker-compose.yaml` и `prometeus.yaml`. Эти файлы были загружены в личный репозиторий и командой 

`git clone https://github.com/etmanov11/etmanov_d_e.git`

устанавливаем их в папку `grafana_stack_for_docker`.

![image](https://github.com/user-attachments/assets/39831f2a-1fd0-4512-854a-510ce19310ac)

Перед выполнением следующих шагов нужно сохранить файл `docker-compose.yaml` в другой папке, чтобы в случае неправильной работы нового файла можно было восстановить старый и работать с ним. Копируем файл `docker-compose.yaml` командой

`cp docker-compose.yaml /home/etmanov`

![image](https://github.com/user-attachments/assets/ccf135f6-bbfa-416d-9622-cbb054d38bde)

Теперь заменим файл `docker-compose.yaml` на другой файл `docker-compose.yaml` командой 

`mv docker-compose.yaml /home/etmanov/grafana_stack_for_docker/docker-compose.yaml`

![image](https://github.com/user-attachments/assets/a1255f99-0c7e-4b8d-9ab1-da762f729b1a)

После этого переходим в папку `/mnt/common_volume/swarm/grafana/config` командой 

`cd /mnt/common_volume/swarm/grafana/config`,

в которой находится файл `prometheus.yaml`

![image](https://github.com/user-attachments/assets/ad380954-2a9e-4297-afed-4a2563c64059)

Следующим шагом открывает файл `prometheus.yaml` в редакторе vim командой 

`vi prometheus.yaml`

и меняем в списке `targets` первую переменную на `exporter:9100`

![image](https://github.com/user-attachments/assets/df18763e-066c-4cc7-a0e9-2cbd7160ae41)

![image](https://github.com/user-attachments/assets/69c6eeff-917e-4086-aef1-c53c21cd53e0)

После этого нужно нажать Esc -> Shift + : -> ввести wq! -> Enter, чтобы выйти из редактора vim с сохранением.

Перемещаем файл prometheus.yaml в /mnt/common_volume/swarm/grafana/config/ заменяя предыдущий файл командой

`sudo mv prometheus.yaml /mnt/common_volume/swarm/grafana/config/`

Теперь запускаем контейнеры, определенные в файле `docker-compose.yml` командой 

`sudo docker compose up -d`

![image](https://github.com/user-attachments/assets/7d2fd40c-1486-4358-b9ea-544eb8f10a52)

После этого переходим в браузер и в поисковой строке вводим 

`localhost:3000`

![image](https://github.com/user-attachments/assets/09df10bd-5dab-48f2-9e29-7d1fec4895ca)

После того как зашли в главное меню, нужно создать `Dashboards`. Все необходимые шаги показаны ниже.

![image](https://github.com/user-attachments/assets/bbaf7f61-6b47-4879-94bf-f6117e788c74)

![image](https://github.com/user-attachments/assets/67761ca5-a142-42e0-8922-3a0d67a61ed1)

![image](https://github.com/user-attachments/assets/ee47952b-418a-4871-a8e0-2cb7c87c3dd2)

![image](https://github.com/user-attachments/assets/00d3dca2-4661-48a0-81a5-cdc64cde0c8e)

![image](https://github.com/user-attachments/assets/1eb3a316-687a-488f-a519-73d5d611e9ae)

![image](https://github.com/user-attachments/assets/1c6a5ff4-6d57-43ef-945e-f6fbe3d8047b)

![image](https://github.com/user-attachments/assets/2ea58ef7-69ee-4d97-9d75-0dbd324b33fb)

После того, как все шаги выполнены, можем увидеть результат проделанной работы.

![image](https://github.com/user-attachments/assets/da80cd9f-3b16-45b8-a53b-40bfc4be5517)

__6 пара__

Для начала переходим в нужную директорию и запускаем контейнеры командой 

`sudo docker compose up -d`

![image](https://github.com/user-attachments/assets/27fff95b-6b6c-4e95-95f5-2122122710cf)

Теперь вводим команду 

`echo -e "# TYPE light_metric1 gauge\nlight_metric1 20" | curl --data-binary @- http://localhost:8428/api/v1/import/prometheus`

![image](https://github.com/user-attachments/assets/7a72a9a6-da94-4a72-ab7d-1f019ed4e7e6)

После этого переходим в браузер и в поисковой строке вводим 

`localhost:3000`

Создаем новый `dashboard` 

![image](https://github.com/user-attachments/assets/08e59480-ad1f-4243-9268-a1f2513c7fb1)

Теперь выбираем вкладку `code` и ввыдим переменную `light_metric1`, после чего нажимаем `Run queries` и перехом в новую вкладку, нажав `Apply`.

![image](https://github.com/user-attachments/assets/c553b145-007f-4176-a03d-8534316501f0)

В командной строке вводим команду 

`echo -e "# TYPE light_metric1 gauge\nlight_metric1 10" | curl --data-binary @- http://localhost:8428/api/v1/import/prometheus`

Чтобы изменить значение переменной

А затем команду 

`echo -e "# TYPE light_metric1 gauge\nlight_metric1 15" | curl --data-binary @- http://localhost:8428/api/v1/import/prometheus`

Чтобы снова изменить значение переменной. Делаем эти шаги для того чтобы отследить изменения на графике.

![image](https://github.com/user-attachments/assets/ad52493c-9d14-4d64-ad8f-c107fa005839)

После проделанных шагов можем увидеть результат на графике

![image](https://github.com/user-attachments/assets/4e1bb05d-6c5f-4892-b5e2-822dce2e6c66)

Далее нужно поменять значение переменной `Connect null values` на `Always`. После чего сохранить и увидеть результат.

![image](https://github.com/user-attachments/assets/1fbb49b1-1c2b-4f31-8b6b-f15927fe8b9a)

![image](https://github.com/user-attachments/assets/1537a30d-9607-40ad-ac58-f2bfa8564079)













