<h3> Задание 1 </h3>

![alt text](https://github.com/Nildi/homework/blob/main/sflt_hw1.1.png)
![alt text](https://github.com/Nildi/homework/blob/main/sflt_hw1.3.png)
![alt text](https://github.com/Nildi/homework/blob/main/sflt_hw1.2.png)
![Ссылка на файл](https://github.com/Nildi/homework/blob/main/hsrp_advanced_hw.pkt )

<h3> Задание 2 </h3>

![alt text](https://github.com/Nildi/homework/blob/main/sflt_hw2.1.png)
![alt text](https://github.com/Nildi/homework/blob/main/sflt_hw2.2.png)
![alt text](https://github.com/Nildi/homework/blob/main/sflt_hw2.3.png)
![alt text](https://github.com/Nildi/homework/blob/main/sflt_hw2.4.png)
![Конфигурационный файл](https://github.com/Nildi/homework/blob/main/keepalived.conf)
#!/bin/bash
if [[ $(netstat -tuln | grep LISTEN | grep :80) ]] && [[ -f /var/www/html/index.nginx-debian.html ]]; then
        exit 0
else
        sudo systemctl stop keepalived
fi
