<h1> Борисова К.Р. К-ИСП-39-1 </h1> 

АИС (Автоматизированной Информационной Системы)

![image](https://github.com/user-attachments/assets/079ecc14-8b07-4d55-aff2-41dac92cf19c)  

Начинаем с установки пакета wget (утилиты командной строки Linux, используемой для загрузки файлов из интернета), используя команду <code>sudo yum install wget</code>  

![image](https://github.com/user-attachments/assets/12b55244-1be3-48ac-b02a-21094399553e)  

После чего устанавливаем пакеты curl командой <code>sudo yum install curl</code>

![image](https://github.com/user-attachments/assets/41711237-f6ea-466c-9c84-fb84392c4d60)

Командой <code>sudo wget -P /etc/yum.repos.d/ https://download.docker.com/linux/centos/docker-ce.repo</code> скачиваем репозиторий 

![image](https://github.com/user-attachments/assets/993f5fc2-2883-4246-99e0-f939812ded11)

После чего командой <code>sudo yum install docker-ce docker-ce-cli containerd.io</code> устанавливаем docker 

![image](https://github.com/user-attachments/assets/54275fb1-6eef-4ca4-a82a-a63481928c35)

