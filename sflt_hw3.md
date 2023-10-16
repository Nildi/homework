<h3> Задание 1 </h3>

![alt text](https://github.com/Nildi/homework/blob/main/sflt_hw3.1.1.png)
![alt text](https://github.com/Nildi/homework/blob/main/sflt_hw3.1.2.png)
rsync -ac --exclude=".*/" . /tmp/backup

<h3> Задание 2 </h3>

![alt text](https://github.com/Nildi/homework/blob/main/sflt_hw3.2.1.png)
0 0 * * * /home/night/backup.sh

!#/bin/bash
rsync -a --checksum --exclude=".*" /home/devops/ /tmp/backup

if [ $? -eq 0 ]; then
    echo "Success" >> /var/log/backup.log
else
    echo "Failed" >> /var/log/backup.log
fi
