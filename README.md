<h1> Борисова К.Р. К-ИСП-39-1 </h1> 

АИС (Автоматизированной Информационной Системы)

![image](https://github.com/user-attachments/assets/079ecc14-8b07-4d55-aff2-41dac92cf19c)  

Начинаем с установки пакета wget (утилиты командной строки Linux, используемой для загрузки файлов из интернета), используя команду <code>sudo yum install wget</code>: 

![image](https://github.com/user-attachments/assets/12b55244-1be3-48ac-b02a-21094399553e)  

После чего устанавливаем пакеты curl командой <code>sudo yum install curl</code>:

![image](https://github.com/user-attachments/assets/41711237-f6ea-466c-9c84-fb84392c4d60)

Командой <code>sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo</code> скачиваем репозиторий:

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

![image](https://github.com/user-attachments/assets/336ae0a2-6d11-4e4c-9cd2-1760bcf521a3)

Переходим <code>cd grafana_stack_for_docker</code> в папку grafana_stack_for_docker:

![image](https://github.com/user-attachments/assets/52489032-5137-4c12-b64a-8f53e9c8249e)

Командой <code>sudo mkdir -p /mnt/common_volume/swarm/grafana/config</code> создаём директорию для конфигурации Grafana

![image](https://github.com/user-attachments/assets/04259fb6-e061-49fe-8672-d7abbae827f6)

Создает несколько директорий Grafana одновременно 
<code>sudo mkdir -p /mnt/common_volume/grafana/{grafana-config,grafana-data,prometheus-data}</code>:

![image](https://github.com/user-attachments/assets/98b0a958-9f50-49b1-bf77-35cea43d743b)



