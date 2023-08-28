<h3> Задание 1 </h3>

![alt text](https://github.com/Nildi/homework/blob/main/smon-homework02.png)


#апдейт кэша и инсталляция postgresql
apt update
apt install postgresql

#подключение репозитория заббикс и апдейт кэша
wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4+debian11_all.deb
dpkg -i zabbix-release_6.0-4+debian11_all.deb
apt update 

#установка сервера заббикс и его компонентов
apt install zabbix-server-pgsql zabbix-frontend-php php7.4-pgsql zabbix-apache-conf zabbix-sql-scripts

#подготовка базы
sudo -u postgres createuser --pwprompt zabbix
sudo -u postgres createdb -O zabbix zabbix 
zcat /usr/share/zabbix-sql-scripts/postgresql/server.sql.gz | sudo -u zabbix psql zabbix

#добавление пароля для подключения к БД в конфиг заббикса
sed -i 's/# DBPassword=/DBPassword=netology2023/g' /etc/zabbix/zabbix_server.conf

#перезапуск сервера заббикс, вебсервера и добавление их в автозагрузку
systemctl restart zabbix-server apache2
systemctl enable zabbix-server apache2 

<h3>  Задание 2 </h3>

![alt text](https://github.com/Nildi/homework/blob/main/smon_hw2.2.png)
![alt text](https://github.com/Nildi/homework/blob/main/smon_hw2.3.png)
![alt text](https://github.com/Nildi/homework/blob/main/smon_hw2.4.png)



#подключение репозитория заббикс и апдейт кэша
wget https://repo.zabbix.com/zabbix/6.0/debian/pool/main/z/zabbix-release/zabbix-release_6.0-4+debian11_all.deb
dpkg -i zabbix-release_6.0-4+debian11_all.deb
apt update  

#установка агента заббикс
apt install zabbix-agent

#перезапуск агента заббикс и добавление в автозагрузку
systemctl restart zabbix-agent
systemctl enable zabbix-agent 

#просмотр логов агента, правка сервера в конфиге агента и его перезапуск
tail -f /var/log/zabbix/zabbix_agentd.log
nano /etc/zabbix/zabbix_agentd.conf
systemctl restart zabbix-agent
