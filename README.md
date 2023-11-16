# Jarkom-Modul-3-I05-2023

## Modul 3 Jarkom 2023 I05 Formal Report

Group Members:
| No |  Name    |  NRP  |
| ---       |   ---     |---  |
|     1     |     Khairiya Maisa Putri    | 5025211192 |
|     2     |     Talitha Hayyinas Sahala    |  5025211263 |

## Topologi

## Node Configurations

- **Aura : Router (DHCP Relay)**
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 10.61.1.1
	netmask 255.255.255.0

auto eth2
iface eth2 inet static
	address 10.61.2.1
	netmask 255.255.255.0

auto eth3
iface eth3 inet static
	address 10.61.3.1
	netmask 255.255.255.0

auto eth4
iface eth4 inet static
	address 10.61.4.1
	netmask 255.255.255.0
```
- **Himmel : DHCP Server**
```
auto eth0
iface eth0 inet static
	address 10.61.1.2
	netmask 255.255.255.0
	gateway 10.61.1.1
```
- **Heiter : DNS Server**
```
auto eth0
iface eth0 inet static
	address 10.61.1.3
	netmask 255.255.255.0
	gateway 10.61.1.1
```
- **Denken : Database Server**
```
auto eth0
iface eth0 inet static
    address 10.61.2.2
    netmask 255.255.255.0
    gateway 10.61.2.1
```
- **Eisen : Load Balancer**
```
auto eth0
iface eth0 inet static
	address 10.61.2.3
	netmask 255.255.255.0
	gateway 10.61.2.1
```
- **Frieren : Laravel Worker**
```
auto eth0
iface eth0 inet static
	address 10.61.4.4
	netmask 255.255.255.0
	gateway 10.61.4.1
```
- **Flamme : Laravel Worker**
```
auto eth0
iface eth0 inet static
	address 10.61.4.5
	netmask 255.255.255.0
	gateway 10.61.4.1
```
- **Fern : Laravel Worker**
```
auto eth0
iface eth0 inet static
	address 10.61.4.6
	netmask 255.255.255.0
	gateway 10.61.4.1
```
- **Lawine : PHP Worker**
```
auto eth0
iface eth0 inet static
	address 10.61.3.4
	netmask 255.255.255.0
	gateway 10.61.3.1
```
- **Linie : PHP Worker**
```
auto eth0
iface eth0 inet static
	address 10.61.3.5
	netmask 255.255.255.0
	gateway 10.61.3.1
```
- **Lugner : PHP Worker**
```
auto eth0
iface eth0 inet static
	address 10.61.3.6
	netmask 255.255.255.0
	gateway 10.61.3.1
```
- **Revolte : Client**
```
auto eth0
iface eth0 inet dhcp
```
- **Richter : Client**
```
auto eth0
iface eth0 inet dhcp
```
- **Sein : Client**
```
auto eth0
iface eth0 inet dhcp
```
- **Stark : Client**
```
auto eth0
iface eth0 inet dhcp
```

## Preparation
On every nodes, edit the ```.bashrc``` file using ```nano``` command, where we write ```bash /root/script.sh``` inside it. And then inside the ```script.sh``` file we write some needed commands for each nodes, like these:

- **Himmel : DHCP Server**
```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf

apt-get update
apt-get install isc-dhcp-server -y
cp -r -f /root/prak3/etc /
service isc-dhcp-server restart
```
- **Heiter : DNS Server**
```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf

apt-get update
apt-get install bind9 -y
cp -r -f /root/prak3/etc /
service bind9 restart
```
- **Aura : Router (DHCP Relay)**
```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf

apt-get update
apt-get install isc-dhcp-relay -y
service isc-dhcp-relay start
cp -r -f /root/prak3/etc /
service isc-dhcp-relay restart
```
- **Denken : Database Server**
```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf

cp -r -f /root/prak3/etc /
```
- **Eisen : Load Balancer**
```
cp -r -f /root/prak3/etc /

echo nameserver 192.168.122.1 > /etc/resolv.conf
apt-get update
apt install nginx php php-fpm -y
service php7.3-fpm status
```
- **Frieren : Laravel Worker**
```
echo nameserver 192.168.122.1 > /etc/resolv.conf

cp -r -f /root/prak3/etc /
```
- **Flamme : Laravel Worker**
```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf

cp -r -f /root/prak3/etc /
```
- **Fern : Laravel Worker**
```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf

cp -r -f /root/prak3/etc /
```
- **Lawine : PHP Worker**
```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf

cp -r -f /root/prak3/etc /

apt-get update
apt-get install php php-fpm
service php7.3-fpm status
apt-get install wget
apt-get install unzip

wget --no-check-certificate 'https://drive.usercontent.google.com/download?id=1$
unzip granz.channel.I05.com
cp -r modul-3/ /var/www
rm -r modul-3

ln -s /etc/nginx/sites-available/jarkom /etc/nginx/sites-enabled
rm -r /etc/nginx/sites-enabled/default

service nginx reload
service nginx restart

service php7.3-fpm start
service php7.3-fpm restart
```
- **Linie : PHP Worker**
```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf

cp -r -f /root/prak3/etc /

apt-get update
apt-get install php php-fpm
service php7.3-fpm status
apt-get install wget
apt-get install unzip

wget --no-check-certificate 'https://drive.usercontent.google.com/download?id=1$
unzip granz.channel.I05.com
cp -r modul-3/ /var/www
rm -r modul-3

ln -s /etc/nginx/sites-available/jarkom /etc/nginx/sites-enabled
rm -r /etc/nginx/sites-enabled/default

service nginx reload
service nginx restart

service php7.3-fpm start
service php7.3-fpm restart
```
- **Lugner : PHP Worker**
```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf

cp -r -f /root/prak3/etc /

apt-get update
apt-get install php php-fpm
service php7.3-fpm status
apt-get install wget
apt-get install unzip

wget --no-check-certificate 'https://drive.usercontent.google.com/download?id=1$
unzip granz.channel.I05.com
cp -r modul-3/ /var/www
rm -r modul-3

ln -s /etc/nginx/sites-available/jarkom /etc/nginx/sites-enabled
rm -r /etc/nginx/sites-enabled/default

service nginx reload
service nginx restart

service php7.3-fpm start
service php7.3-fpm restart
```
- **Revolte : Client**
```
echo nameserver 192.168.122.1 > /etc/resolv.conf

apt-get install apache2
service apache2 start

cp -r -f /root/prak3/etc /

apt install lynx -y
```
- **Richter : Client**
```
cp -r -f /root/prak3/etc /
```
- **Sein : Client**
```
cp -r -f /root/prak3/etc /
```
- **Stark : Client**
```
cp -r -f /root/prak3/etc /
```
# No. 1
> Lakukan konfigurasi sesuai dengan peta yang sudah diberikan.

# No. 2
> Semua CLIENT harus menggunakan konfigurasi dari DHCP Server.
Client yang melalui Switch3 mendapatkan range IP dari [prefix IP].3.16 - [prefix IP].3.32 dan [prefix IP].3.64 - [prefix IP].3.80

# No. 3
> Client yang melalui Switch4 mendapatkan range IP dari [prefix IP].4.12 - [prefix IP].4.20 dan [prefix IP].4.160 - [prefix IP].4.168

# No. 4
> Client mendapatkan DNS dari Heiter dan dapat terhubung dengan internet melalui DNS tersebut

# No. 5
> Lama waktu DHCP server meminjamkan alamat IP kepada Client yang melalui Switch3 selama 3 menit sedangkan pada client yang melalui Switch4 selama 12 menit. Dengan waktu maksimal dialokasikan untuk peminjaman alamat IP selama 96 menit 

# No. 6
> Pada masing-masing worker PHP, lakukan konfigurasi virtual host untuk website berikut dengan menggunakan php 7.3.
# No. 7
> Kepala suku dari Bredt Region memberikan resource server sebagai berikut:
Lawine, 4GB, 2vCPU, dan 80 GB SSD.
Linie, 2GB, 2vCPU, dan 50 GB SSD.
Lugner 1GB, 1vCPU, dan 25 GB SSD.
aturlah agar Eisen dapat bekerja dengan maksimal, lalu lakukan testing dengan 1000 request dan 100 request/second.

# No. 8
> Karena diminta untuk menuliskan grimoire, buatlah analisis hasil testing dengan 200 request dan 10 request/second masing-masing algoritma Load Balancer dengan ketentuan sebagai berikut:
Nama Algoritma Load Balancer,
Report hasil testing pada Apache Benchmark,
Grafik request per second untuk masing masing algoritma, 
Analisis 

# No. 9
> Dengan menggunakan algoritma Round Robin, lakukan testing dengan menggunakan 3 worker, 2 worker, dan 1 worker sebanyak 100 request dengan 10 request/second, kemudian tambahkan grafiknya pada grimoire.

# No. 10
> Selanjutnya coba tambahkan konfigurasi autentikasi di LB dengan dengan kombinasi username: “netics” dan password: “ajkyyy”, dengan yyy merupakan kode kelompok. Terakhir simpan file “htpasswd” nya di /etc/nginx/rahasisakita/

# No. 11
> Lalu buat untuk setiap request yang mengandung /its akan di proxy passing menuju halaman https://www.its.ac.id.

# No. 12
> Selanjutnya LB ini hanya boleh diakses oleh client dengan IP [Prefix IP].3.69, [Prefix IP].3.70, [Prefix IP].4.167, dan [Prefix IP].4.168.

# No. 13
> Semua data yang diperlukan, diatur pada Denken dan harus dapat diakses oleh Frieren, Flamme, dan Fern.

# No. 14
> Frieren, Flamme, dan Fern memiliki Riegel Channel sesuai dengan quest guide berikut. Jangan lupa melakukan instalasi PHP8.0 dan Composer

# No. 15
> Riegel Channel memiliki beberapa endpoint yang harus ditesting sebanyak 100 request dengan 10 request/second. Tambahkan response dan hasil testing pada grimoire.
POST /auth/register 

# No. 16
> Riegel Channel memiliki beberapa endpoint yang harus ditesting sebanyak 100 request dengan 10 request/second. Tambahkan response dan hasil testing pada grimoire.
POST /auth/login

# No. 17
> Riegel Channel memiliki beberapa endpoint yang harus ditesting sebanyak 100 request dengan 10 request/second. Tambahkan response dan hasil testing pada grimoire. 
GET /me

# No. 18
> Untuk memastikan ketiganya bekerja sama secara adil untuk mengatur Riegel Channel maka implementasikan Proxy Bind pada Eisen untuk mengaitkan IP dari Frieren, Flamme, dan Fern.

# No. 19
> Untuk meningkatkan performa dari Worker, coba implementasikan PHP-FPM pada Frieren, Flamme, dan Fern. Untuk testing kinerja naikkan pm.max_children, pm.start_servers, pm.min_spare_servers, pm.max_spare_servers.
sebanyak tiga percobaan dan lakukan testing sebanyak 100 request dengan 10 request/second kemudian berikan hasil analisisnya pada Grimoire.

# No. 20
> Nampaknya hanya menggunakan PHP-FPM tidak cukup untuk meningkatkan performa dari worker maka implementasikan Least-Conn pada Eisen. Untuk testing kinerja dari worker tersebut dilakukan sebanyak 100 request dengan 10 request/second.