# Cara Menginstall Telnet pada Kali Linux WSL
### Jalankan perintah
```bash
sudo apt update
```
### Kemudian Install telnetd dan xinetd
```bash
sudo apt install xinetd telnetd
```
### Kemudian Konfigurasi xinetd
```bash
sudo nano /etc/xinetd.conf
```
masukkan
```
defaults
{
   instances = 60
   log_type = SYSLOG authpriv
   log_on_success = HOST PID
   log_on_failure = HOST
   cps = 25 30
}
```
### Kemudian Konfigurasi Telnet pada xinetd
eksekusi printah berikut
```bash
sudo nano /etc/xinetd.d/telnet
```
masukkan
``` bash
service telnet
{
   disable = no
   flags           = REUSE
   socket_type     = stream
   wait            = no
   user            = root
   server          = /usr/sbin/in.telnetd
   log_on_failure  += USERID
}
```
### yang terakhir coba restart xinetd
```bash
sudo service xinetd restart
```
# Selesai!!!, Sekarang Kamu bisa Mencoba
```bash
telnet localhost
```
