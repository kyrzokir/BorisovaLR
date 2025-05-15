<h1> Борисова К.Р. К-ИСП-39-1 </h1> 

АИС (Автоматизированной Информационной Системы)

![image](https://github.com/user-attachments/assets/079ecc14-8b07-4d55-aff2-41dac92cf19c)  

Начинаем с установки пакета wget (утилиты командной строки Linux, используемой для загрузки файлов из интернета), используя команду <code>sudo yum install wget</code>: 

![image](https://github.com/user-attachments/assets/12b55244-1be3-48ac-b02a-21094399553e)  

После чего устанавливаем пакеты curl командой <code>sudo yum install curl</code>:

![image](https://github.com/user-attachments/assets/41711237-f6ea-466c-9c84-fb84392c4d60)

Командой <code>sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo</code> скачиваем репозиторий с docker:

![image](https://github.com/user-attachments/assets/993f5fc2-2883-4246-99e0-f939812ded11)

После чего командой <code>sudo yum install docker-ce docker-ce-cli containerd.io</code> устанавливаем docker:

![image](https://github.com/user-attachments/assets/54275fb1-6eef-4ca4-a82a-a63481928c35)

После чего запускаем docker и разрешаем автозапуск <code>sudo systemctl enable docker --now</code>:

![image](https://github.com/user-attachments/assets/d75d4699-eade-4287-ab46-c32fc64cf449)

Командой  <code>COMVER=$(curl -s https://api.github.com/repos/docker/compose/releases/latest | grep 'tag_name' | cut -d\" -f4)</code> смотрим последнюю версию docker-compose при помощи api github:

![image_2025-05-15_13-57-59](https://github.com/user-attachments/assets/af42c978-60bf-490e-8008-5f12157308a7)

При помощи команды <code>sudo curl -L "https://github.com/docker/compose/releases/download/$COMVER/docker-compose-$(uname -s)-$(uname -m)" -o /usr/bin/docker-compose</code> устанавливаем docker-compose последней версии:

![image](https://github.com/user-attachments/assets/7af5c941-64a5-4e50-8f6d-58843a2b6a90)

Командой <code>sudo chmod +x /usr/bin/docker-compose</code> делаем docker-compose исполняемым и даём ему права доступа:

![image (2)](https://github.com/user-attachments/assets/4daeadd3-19fd-439a-b663-163537cfb9ac)

Командой <code>docker-compose --version</code> узнаём версию docker-compose:

![image](https://github.com/user-attachments/assets/f4aebbc6-1f3c-47a1-8686-c3f6bb324864)

Скачиваем пакет git и клонируем репозиторий rafana_stack_for_docker с GitHub, командой <code>git clone https://github.com/skl256/grafana_stack_for_docker.git</code>:

![image](https://github.com/user-attachments/assets/1675f672-1f83-41e3-8c37-de54197bf8d5)

Переходим <code>cd grafana_stack_for_docker</code> в папку grafana_stack_for_docker:

![image](https://github.com/user-attachments/assets/52489032-5137-4c12-b64a-8f53e9c8249e)

Командой <code>sudo mkdir -p /mnt/common_volume/swarm/grafana/config</code> создаём директорию для конфигурации Grafana:

![image](https://github.com/user-attachments/assets/04259fb6-e061-49fe-8672-d7abbae827f6)

Создает несколько директорий Grafana одновременно командой
<code>sudo mkdir -p /mnt/common_volume/grafana/{grafana-config,grafana-data,prometheus-data}</code>:

![image](https://github.com/user-attachments/assets/98b0a958-9f50-49b1-bf77-35cea43d743b)

Меняем владельца директорий на текущего пользователя командой <code>sudo chown -R $(id -u):$(id -g) {/mnt/common_volume/swarm/grafana/config,/mnt/common_volume/grafana}</code>:

![image](https://github.com/user-attachments/assets/daffa7ce-309b-418f-83f0-73600163d073)

Создает файл <code>grafana.ini</code> в указанной директории командой <code>touch /mnt/common_volume/grafana/grafana-config/grafana.ini</code>:

![image](https://github.com/user-attachments/assets/40520d83-8afc-4509-bdf7-deb33b93318b)

Копирует все файлы из директории config в <code>/mnt/common_volume/swarm/grafana/config/</code> командой <code>cp config/* /mnt/common_volume/swarm/grafana/config/</code>:

![image](https://github.com/user-attachments/assets/b1e9d260-1529-45ba-8e84-d608d0931c2f)

Переименовываем файл grafana.yaml в docker-compose.yaml командой <code>mv grafana.yaml docker-compose.yaml</code>:

![image](https://github.com/user-attachments/assets/3663f187-c1a6-481f-ac2c-001bc71e83e7)

Запускаем docker в фоновом режие командой <code>sudo docker compose up -d</code>:

![image](https://github.com/user-attachments/assets/5c68548c-9579-42ac-8651-e2bb7a6821ab)

Командой <code>sudo vi docker-compose.yaml</code> открываем файл <code>sudo vi docker-compose.yaml</code> и редактируем содержимое:

![image](https://github.com/user-attachments/assets/e03806f5-cd35-49fc-9de0-a58a81414669)

Так-же изменяем файл <code>prometheus.yaml</code>:

![image](https://github.com/user-attachments/assets/0a8d9734-05f0-4f17-9139-d760fb6daab7)

Командой <code>sudo docker compose up -d</code> запускаем docker compose:

![image](https://github.com/user-attachments/assets/6ab05d51-5fbb-460f-9722-f97b601c0ecc)

Останавливаем контейнеры командой <code>sudo docker compose stop</code>:

![image](https://github.com/user-attachments/assets/5e505478-f29b-4c90-b5c3-1a014ab96757)

Останавливаем и удаляем контейнеры командой <code>sudo docker compose down</code>:

![image](https://github.com/user-attachments/assets/98398ddb-217c-4cce-a13d-45fd959ee5e4)

Смотрим текущее состояние командой <code>sudo docker compose ps</code>:

![image](https://github.com/user-attachments/assets/9cd70658-3603-4b25-a025-acc7173e1c21)


Клонируем репозиторий GitHub себе командой <code>https://github.com/kyrzokir/BorisovaLR.git</code>:

![image](https://github.com/user-attachments/assets/b246680a-df17-4d4f-8c93-6ed42ba67a24)

<h1>Graphana</h1>

Открываем браузер и преходим в <code>localhost3000</code> и вводим в логин и пароль admin:

![image](https://github.com/user-attachments/assets/17706672-ffe8-45bf-978c-8a05ece60f14)

Переходим в <code>Dash board</code> и нажимаем на <code>Add visualization</code>:

![image](https://github.com/user-attachments/assets/a4e0bda9-88e2-4b1e-9ddc-1a69fbed494d)

Выбираем Prometheus:

![image](https://github.com/user-attachments/assets/aaf0cc6e-8626-495c-8fdb-32149309df16)

Заполняем данные и проверяем:

![image](https://github.com/user-attachments/assets/3603f821-3a9a-41e1-bd62-8e3e873e955d)
![image](https://github.com/user-attachments/assets/c016de6d-1bd1-4794-9dbb-6ba43ee1f9c3)

Заходим в <code>Import a dashboard</code> и вводим <code>1860</code>:

![image](https://github.com/user-attachments/assets/fbf09e59-7015-4b90-ab3d-d82856e4c38e)

![image](https://github.com/user-attachments/assets/2f4d2c11-3e85-407f-81de-24b1cb18647c)

И смотрим на результат:

![image](https://github.com/user-attachments/assets/500f8c5e-ce6a-4cad-98ee-5f8bff4cbed1)

<h1>VictoriaMetrics</h1>

Запускаем сервер командой <code>sudo docker compose up -d</code>:

![image](https://github.com/user-attachments/assets/23bdf593-6c31-4a56-8020-17c50d2f4d6d)

Переходим  по <code>localhost:3000</code> и создаём VictoriaMetrics, после чего проверяем:

![image](https://github.com/user-attachments/assets/bbba2f2e-6339-4969-a9b1-14cd29ccda7a)

![image](https://github.com/user-attachments/assets/1b91fa20-2b43-4dc7-bdc2-87d23927ba1d)

![image](https://github.com/user-attachments/assets/d425cb79-02be-405f-b413-a0e095e48e4c)

Дальше в терминале прописываем команду <code>echo -e "# TYPE light_metric1 gauge\nlight_metric1 0" | curl --data-binary @- http://localhost:8428/api/v1/import/prometheus</code>:

![image](https://github.com/user-attachments/assets/3a39db4a-9e13-45b1-bef2-6b671761100d)

Переходим по ссылке <code>http://localhost:8428/api/v1/query</code>:

![image](https://github.com/user-attachments/assets/5990c3b1-8bf4-40d7-a2a0-40453034807a)

После чего по <code>http://localhost:8428</code>:

![image](https://github.com/user-attachments/assets/40a3cd12-2442-45df-b62c-ae980952c564)

Выбираем <code>vmui</code> и в строке пишем <code>light_metric1</code> и видим точку на графике:

![image](https://github.com/user-attachments/assets/82474a1a-1bea-497d-a8ec-a50976fa97b4)

Переходим на <code>localhost:3000</code>, DashBoard и вводим light_metric1:

![image](https://github.com/user-attachments/assets/737295c7-cde9-45fb-8e44-5d2759127584)






















