
nikita@nikita-VirtualBox:~$ sudo iptables - L
Bad argument `-'
Try `iptables -h' or 'iptables --help' for more information.
nikita@nikita-VirtualBox:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
nikita@nikita-VirtualBox:~$ sudo -A INPUT -i etho -p tcp --dport 80 -j ACCEPT
sudo: INPUT: команда не найдена
nikita@nikita-VirtualBox:~$ sudo iptables -A INPUT -i etho -p tcp --dport 80 -j ACCEPT
nikita@nikita-VirtualBox:~$ sudo iptables -A INPUT -i etho -p tcp --dport 20 -j ACCEPT
nikita@nikita-VirtualBox:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ftp-data

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
nikita@nikita-VirtualBox:~$ sudo iptables -L -t nat
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
nikita@nikita-VirtualBox:~$ sudo iptables -t nat -I PREROUTING -p tcp --dport 80 -j REDIRECT --to-port 8080
nikita@nikita-VirtualBox:~$ sudo iptables -L -t nat
Chain PREROUTING (policy ACCEPT)
target     prot opt source               destination         
REDIRECT   tcp  --  anywhere             anywhere             tcp dpt:http redir ports 8080

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         

Chain POSTROUTING (policy ACCEPT)
target     prot opt source               destination         
nikita@nikita-VirtualBox:~$ sudo iptables -A INPUT -i etho -p tcp -s 3.4.5.6. -j DROP
iptables v1.8.7 (nf_tables): host/network `3.4.5.6.' not found
Try `iptables -h' or 'iptables --help' for more information.
nikita@nikita-VirtualBox:~$ sudo iptables -A INPUT -i etho -p tcp -s 3.4.5.6. -j DROP
iptables v1.8.7 (nf_tables): host/network `3.4.5.6.' not found
Try `iptables -h' or 'iptables --help' for more information.
nikita@nikita-VirtualBox:~$ sudo iptables -A INPUT -i etho -p tcp -s 3.4.5.6. -j DROP
iptables v1.8.7 (nf_tables): host/network `3.4.5.6.' not found
Try `iptables -h' or 'iptables --help' for more information.
nikita@nikita-VirtualBox:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:http
ACCEPT     tcp  --  anywhere             anywhere             tcp dpt:ftp-data

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
nikita@nikita-VirtualBox:~$ sudo iptables -L -F nat
iptables v1.8.7 (nf_tables): Cannot use -F with -L

Try `iptables -h' or 'iptables --help' for more information.
nikita@nikita-VirtualBox:~$ sudo iptables -F -t nat
nikita@nikita-VirtualBox:~$ sudo iptables -F 
nikita@nikita-VirtualBox:~$ sudo iptables -L
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination         
nikita@nikita-VirtualBox:~$ 
