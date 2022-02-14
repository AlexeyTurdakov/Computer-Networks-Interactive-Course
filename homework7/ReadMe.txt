netstat -t
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address Foreign Address State

tcp 0 0 MackBook4.1:34298 geekbrains.ru:https ESTABLISHED
tcp 0 0 MackBook4.1:34278 162.247.243.146:https ESTABLISHED
tcp 0 0 MackBook4.1:34310 geekbrains.ru:https ESTABLISHED
tcp 0 0 MackBook4.1:52306 185.134.203.20:https ESTABLISHED
tcp 0 0 MackBook4.1:38372 s1.ru5.net:https ESTABLISHED
tcp 0 0 MackBook4.1:57794 151.101.114.137:https ESTABLISHED
tcp 0 0 MackBook4.1:33384 ec2-35-157-63-227:https ESTABLISHED
tcp 0 0 MackBook4.1:34300 geekbrains.ru:https ESTABLISHED
tcp 0 0 MackBook4.1:34306 178.248.232.209:https ESTABLISHED
tcp 0 0 MackBook4.1:60498 hem08s06-in-f14.1:https ESTABLISHED
tcp 0 0 MackBook4.1:34308 178.248.232.209:https ESTABLISHED
tcp 0 0 MackBook4.1:34280 162.247.243.146:https ESTABLISHED
tcp 0 0 MackBook4.1:36980 bs.yandex.ru:https ESTABLISHED
tcp 0 0 MackBook4.1:42076 lm-in-f188.1e10:hpvroom ESTABLISHED
tcp 0 0 MackBook4.1:34314 geekbrains.ru:https ESTABLISHED

TCP Заппросы к сайтам с ноутбука. (Ясно видны динамические порты, используеые браузером).

netstat -u
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address Foreign Address State

udp 0 0 MackBook4.1:bootpc _gateway:bootps ESTABLISHED

UDP запрос в сеть.

netstat -tua
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address Foreign Address State

tcp 0 0 0.0.0.0:mysql 0.0.0.0:* LISTEN

tcp 0 0 localhost:5939 0.0.0.0:* LISTEN

tcp 0 0 0.0.0.0:ssh 0.0.0.0:* LISTEN

tcp 0 0 MackBook4.1:34298 geekbrains.ru:https ESTABLISHED
tcp 0 0 MackBook4.1:34278 162.247.243.146:https TIME_WAIT

tcp 0 0 MackBook4.1:34310 geekbrains.ru:https ESTABLISHED
tcp 0 0 MackBook4.1:57794 151.101.114.137:https ESTABLISHED
tcp 0 0 MackBook4.1:33384 ec2-35-157-63-227:https ESTABLISHED
tcp 0 0 MackBook4.1:34300 geekbrains.ru:https ESTABLISHED
tcp 0 0 MackBook4.1:34280 162.247.243.146:https ESTABLISHED
tcp 0 0 MackBook4.1:47136 185.134.201.8:https ESTABLISHED
tcp 0 0 MackBook4.1:42076 lm-in-f188.1e10:hpvroom ESTABLISHED
tcp 0 0 MackBook4.1:34314 geekbrains.ru:https ESTABLISHED
tcp6 0 0 [::]:mysql [::]:* LISTEN

tcp6 0 0 [::]:www-http [::]:* LISTEN

tcp6 0 0 [::]:ssh [::]:* LISTEN

udp 0 0 224.0.0.251:mdns 0.0.0.0:*

udp 0 0 224.0.0.251:mdns 0.0.0.0:*

udp 0 0 MackBook4.1:bootpc _gateway:bootps ESTABLISHED

Все активные запросы и прослушки TCP, UDP.
Тут мы видим и mysql (MariaDB ArchLinux LAMP) на прослушивании порта 3306 стандартного для sql. Так же ssh, apache2 (www-http), mdns запрос.
Слушают порты локальные службы, на удаленные мы обращаемся.

netstat -tua | grep ssh
tcp 0 0 0.0.0.0:ssh 0.0.0.0:* LISTEN

tcp6 0 0 [::]:ssh [::]:* LISTEN

Не имеем подключений.

netstat -tua | grep ssh
tcp 0 0 0.0.0.0:ssh 0.0.0.0:* LISTEN

tcp 0 0 localhost:33680 localhost:ssh ESTABLISHED
tcp 0 0 localhost:ssh localhost:33680 ESTABLISHED
tcp6 0 0 [::]:ssh [::]:* LISTEN

Тут мы открыли локально одно соединение.

netstat -tua | grep ssh
tcp 0 0 0.0.0.0:ssh 0.0.0.0:* LISTEN

tcp 0 0 localhost:33680 localhost:ssh ESTABLISHED
tcp 0 0 MackBook4.1:ssh _gateway:46904 ESTABLISHED
tcp 0 0 localhost:ssh localhost:33680 ESTABLISHED
tcp6 0 0 [::]:ssh [::]:* LISTEN

И тут + одно подключение со смартфона.

netstat -tua | grep ssh
tcp 0 0 0.0.0.0:ssh 0.0.0.0:* LISTEN

tcp 0 0 localhost:33680 localhost:ssh TIME_WAIT

tcp6 0 0 [::]:ssh [::]:* LISTEN

При разрыве коннекта идет ожидание подключения клиентов.
Потом возврат в исходное состояние.

netstat -tua | grep ssh
tcp 0 0 0.0.0.0:ssh 0.0.0.0:* LISTEN

tcp6 0 0 [::]:ssh [::]:* LISTEN

ps -aux | grep ssh
root 401 0.0 0.1 8984 6236 ? Ss 07:39 0:00 sshd: /usr/bin/sshd -D [listener] 0 of 10-100 startups
sergey 576 0.0 0.0 5960 460 ? Ss 07:39 0:00 /usr/bin/ssh-agent -s
sergey 4170 0.6 0.1 12312 5708 pts/2 S+ 10:13 0:00 ssh 127.0.0.1
root 4171 1.0 0.2 13900 9088 ? Ss 10:13 0:00 sshd: sergey [priv]
sergey 4173 0.0 0.1 13900 4712 ? S 10:13 0:00 sshd: sergey@pts/3
sergey 4186 0.0 0.0 6524 2584 pts/1 S+ 10:13 0:00 grep ssh
ps -aux | grep ssh
root 401 0.0 0.1 8984 6236 ? Ss 07:39 0:00 sshd: /usr/bin/sshd -D [listener] 0 of 10-100 startups
sergey 576 0.0 0.0 5960 460 ? Ss 07:39 0:00 /usr/bin/ssh-agent -s
sergey 4192 0.0 0.0 6524 2476 pts/1 S+ 10:14 0:00 grep ssh

При подключении стартует служба и новый процесс для каждого коннекта.