
Verify network connectivity - connect via SSH to your Eve machine and ping 8.8.8.8 

```bash
ssh root@172.16.135.128
# parola e eve
```

Use curl in verbose mode (hint: man curl ) to retrieve example.com - once in HTTP, and once in HTTPS. What's different between the two?

```bash
root@eve-ng:~# curl --verbose http://example.com
*   Trying 104.20.23.154:80...
* Connected to example.com (104.20.23.154) port 80 (#0)
> GET / HTTP/1.1
> Host: example.com
> User-Agent: curl/7.81.0
> Accept: */*
> 
* Mark bundle as not supporting multiuse
< HTTP/1.1 200 OK
< Date: Sun, 18 Oct 2026 14:48:04 GMT
< Content-Type: text/html; charset=utf-8
< Transfer-Encoding: chunked
< Connection: keep-alive
< Server: cloudflare
< Last-Modified: Tue, 13 Oct 2026 20:08:28 GMT
< Allow: GET, HEAD
< Accept-Ranges: bytes
< Age: 0
< cf-cache-status: HIT
< CF-RAY: a4c85785a807b270-FRA
< alt-svc: h3=":443"; ma=86400
< 
<!doctype html><html lang=en><head><meta charset=utf-8><link rel=icon href=data:,><meta name=viewport content="width=device-width,initial-scale=1"><title>Example Domain</title><style>html{color-scheme:light dark;background:light-dark(#eee,#222)}body{font:16px/1.6 system-ui,sans-serif;max-width:26em;margin:auto;padding:25vh 2em 2em;text-align:center}</style></head><body><p>This domain is for use in documentation examples without needing permission. This is not a service; avoid relying on it for testing and monitoring purposes.</p><script src=/s.js></script></body></html>
* Connection #0 to host example.com left intact

```

Si cu https:

```bash
root@eve-ng:~# curl --verbose https://example.com
*   Trying 172.66.147.243:443...
* Connected to example.com (172.66.147.243) port 443 (#0)
* ALPN, offering h2
* ALPN, offering http/1.1
*  CAfile: /etc/ssl/certs/ca-certificates.crt
*  CApath: /etc/ssl/certs
* TLSv1.0 (OUT), TLS header, Certificate Status (22):
* TLSv1.3 (OUT), TLS handshake, Client hello (1):
* TLSv1.2 (IN), TLS header, Certificate Status (22):
* TLSv1.3 (IN), TLS handshake, Server hello (2):
* TLSv1.2 (IN), TLS header, Finished (20):
* TLSv1.2 (IN), TLS header, Supplemental data (23):
* TLSv1.3 (IN), TLS handshake, Encrypted Extensions (8):
* TLSv1.3 (IN), TLS handshake, Certificate (11):
* TLSv1.3 (IN), TLS handshake, CERT verify (15):
* TLSv1.3 (IN), TLS handshake, Finished (20):
* TLSv1.2 (OUT), TLS header, Finished (20):
* TLSv1.3 (OUT), TLS change cipher, Change cipher spec (1):
* TLSv1.2 (OUT), TLS header, Supplemental data (23):
* TLSv1.3 (OUT), TLS handshake, Finished (20):
* SSL connection using TLSv1.3 / TLS_AES_256_GCM_SHA384
* ALPN, server accepted to use h2
* Server certificate:
*  subject: CN=example.com
*  start date: Sep 26 22:49:11 2026 GMT
*  expire date: Dec 25 22:56:35 2026 GMT
*  subjectAltName: host "example.com" matched cert's "example.com"
*  issuer: C=US; O=SSL Corporation; CN=Cloudflare TLS Issuing ECC CA 3
*  SSL certificate verify ok.
* Using HTTP2, server supports multiplexing
* Connection state changed (HTTP/2 confirmed)
* Copying HTTP/2 data in stream buffer to connection buffer after upgrade: len=0
* TLSv1.2 (OUT), TLS header, Supplemental data (23):
* TLSv1.2 (OUT), TLS header, Supplemental data (23):
* TLSv1.2 (OUT), TLS header, Supplemental data (23):
* Using Stream ID: 1 (easy handle 0x5ef1762d9a90)
* TLSv1.2 (OUT), TLS header, Supplemental data (23):
> GET / HTTP/2
> Host: example.com
> user-agent: curl/7.81.0
> accept: */*
> 
* TLSv1.2 (IN), TLS header, Supplemental data (23):
* TLSv1.3 (IN), TLS handshake, Newsession Ticket (4):
* TLSv1.3 (IN), TLS handshake, Newsession Ticket (4):
* old SSL session ID is stale, removing
* TLSv1.2 (IN), TLS header, Supplemental data (23):
* TLSv1.2 (OUT), TLS header, Supplemental data (23):
* TLSv1.2 (IN), TLS header, Supplemental data (23):
* TLSv1.2 (IN), TLS header, Supplemental data (23):
< HTTP/2 200 
< date: Sun, 18 Oct 2026 14:48:24 GMT
< content-type: text/html; charset=utf-8
< server: cloudflare
< last-modified: Tue, 13 Oct 2026 22:05:48 GMT
< allow: GET, HEAD
< accept-ranges: bytes
< age: 2
< cf-cache-status: HIT
< cf-ray: a4c85800fa71d9d8-FRA
< alt-svc: h3=":443"; ma=86400
< 
* TLSv1.2 (IN), TLS header, Supplemental data (23):
<!doctype html><html lang=en><head><meta charset=utf-8><link rel=icon href=data:,><meta name=viewport content="width=device-width,initial-scale=1"><title>Example Domain</title><style>html{color-scheme:light dark;background:light-dark(#eee,#222)}body{font:16px/1.6 system-ui,sans-serif;max-width:26em;margin:auto;padding:25vh 2em 2em;text-align:center}</style></head><body><p>This domain is for use in documentation examples without needing permission. This is not a service; avoid relying on it for testing and monitoring purposes.</p><script src=/s.js></script></body></html>
* TLSv1.2 (IN), TLS header, Supplemental data (23):
* Connection #0 to host example.com left intact

```

Diferenta e ca asta foloeste cev acertificate

Use netcat ( man nc ) to connect to example.com on port 80 and retrieve the page with a manual HTTP request. Yes, type it out yourself. Don't 2 lines of ASCII text win over you.
- How is this different from the curl from exercise 2?

Netcat nu stie protocoae din astea de nivel inalt 
Dupa ce te conectezi faci manual o cerere get si dai enter de 2 ori

În protocolul **HTTP/1.1**, specificația tehnică cere ca marcarea sfârșitului antetelor (_headers_) să se facă prin **două linii goale consecutive** (secvența `CRLF CRLF` sau `\r\n\r\n`).

Iată de ce sunt necesare două apăsări de **Enter**:

1. **Primul Enter:** Finalizează linia curentă a antetului (de exemplu, linia `Host: example.com`). Serverul încă așteaptă, pentru că tu s-ar putea să mai vrei să trimiți și alte antete (cum ar fi `User-Agent: ...` sau `Accept: ...`).
    
2. **Al doilea Enter:** Trmite o **linie goală** (fără niciun text pe ea). Această linie goală îi semnalează serverului: _„Am terminat de trimis antetele, cererea mea este completă, procesează-o!”_.
```bash
root@eve-ng:~# nc example.com 80
GET / HTTP/1.1
Host: example.com

HTTP/1.1 200 OK
Date: Sun, 18 Oct 2026 14:54:53 GMT
Content-Type: text/html; charset=utf-8
Transfer-Encoding: chunked
Connection: keep-alive
Server: cloudflare
Last-Modified: Tue, 13 Oct 2026 20:08:28 GMT
Allow: GET, HEAD
Accept-Ranges: bytes
Age: 4029
cf-cache-status: HIT
CF-RAY: a4c86177fd6b1d8c-FRA
alt-svc: h3=":443"; ma=86400

241
<!doctype html><html lang=en><head><meta charset=utf-8><link rel=icon href=data:,><meta name=viewport content="width=device-width,initial-scale=1"><title>Example Domain</title><style>html{color-scheme:light dark;background:light-dark(#eee,#222)}body{font:16px/1.6 system-ui,sans-serif;max-width:26em;margin:auto;padding:25vh 2em 2em;text-align:center}</style></head><body><p>This domain is for use in documentation examples without needing permission. This is not a service; avoid relying on it for testing and monitoring purposes.</p><script src=/s.js></script></body></html>

0

```

Diferenta e ca trebuie tu sa faci cererea GET ca lumea curl o facea el pt tine

Sau ca sa nu dai enter de 2 ori pui asta in cerere: `Connection: close` la final

Download the following images (if you haven't already): 
- A Linux image for Eve (I used linux-ubuntu-srv-16.04.4-webmin from [here](https://mega.nz/folder/30p3TKob#42_S__9wwPVO0zHIfC4xow) ).
- A router image (I used c7200-adventerprisek9-mz.124-24.T5.image from [here](https://github.com/hegdepavankumar/Cisco-Images-for-GNS3-and-EVE-NG?tab=readme-ov-file#cisco-ios-routers-images-for-eve-ng) .
 Transfer them to your Eve VM (if you haven't already) - you can use croc to make your life easier (instead of scp - but both work).
 
Ok am downloadat niste zipuri
Asa conform documentatie trb sa le ducem pe astea de linux la ceva folder dubios din opt

https://www.eve-ng.net/index.php/documentation/howtos/howto-create-own-linux-host-image/

```bash
cd /opt/unetlab/addons/qemu/

scp linux-ubuntu-srv-16.04.4-webmin.tar.zip root@172.16.135.128:~/
# trb mutat acolo in folderul ala

root@eve-ng:/opt/unetlab/addons/qemu# unzip linux-ubuntu-srv-16.04.4-webmin.tar.zip 
Archive:  linux-ubuntu-srv-16.04.4-webmin.tar.zip
 extracting: linux-ubuntu-srv-16.04.4-webmin.tar.gz  
 
root@eve-ng:/opt/unetlab/addons/qemu# tar -xvf linux-ubuntu-srv-16.04.4-webmin.tar.gz 
linux-ubuntu-srv-16.04.4-webmin/
linux-ubuntu-srv-16.04.4-webmin/virtioa.qcow2

root@eve-ng:/opt/unetlab/addons/qemu# rm -f linux-ubuntu-srv-16.04.4-webmin.tar.gz 
root@eve-ng:/opt/unetlab/addons/qemu# rm -f linux-ubuntu-srv-16.04.4-webmin.tar.zip 
root@eve-ng:/opt/unetlab/addons/qemu# /opt/unetlab/wrappers/unl_wrapper -a fixpermissions

root@eve-ng:/opt/unetlab/addons/qemu
```

**In EVE's GUI, create a project (if you haven't already), give it a name of your choosing (if you find something particularly funny, let us know), and create a node.**

Add new lab e a doua optiune de aici:

![[Pasted image 20261018184234.png]]

Vad ca noduri nu adaugi de aici
![[Pasted image 20261018184351.png]]
Save

WOOOW
![[Pasted image 20261018184411.png]]



 **For now, we will set up 2 Linux machines connected by a router. Use the 2 guides below to set the host images up for usage in Eve projects. For this lab, we only need the Linux one:**
- **Linux**
- **Router** [docs](https://www.eve-ng.net/index.php/documentation/howtos/howto-add-cisco-dynamips-images-cisco-ios/)

Ok deci adaugam un nod apasam pe plus 
Mai intai adaugam reteaua
**Add an object → Network** → alege **Management(Cloud0)**

![[Pasted image 20261018184701.png]]

Apare un norisor in stanga sus

**Add an object → Node** → alegi imaginea Linux, **Number of nodes to add = 2**, apoi folosești valori rezonabile (de exemplu 1 CPU, 1024 MB RAM)

![[Pasted image 20261018184959.png]]

Eu am lasat asa:
![[Pasted image 20261018185146.png]]

Apoi tragi fire spre nor
![[Pasted image 20261018185250.png]]



Te-a mancat in cur sa pui la console type vnc cand ai creat nodurile si acum trb instalat clientul de vnc ca sa iti poata deschide consola

Pe local: 
```bash
sudo apt install -y remmina remmina-plugin-vnc
```

Nu trb sa mai faci nimic doar dai dunlu click pe instanta si broswerul iti deschid eun pop up cu un link
Te duci pe link iti deschide consola

**Parola pt webmin e root si userul tot root**

<mark style="background: #BBFABBA6;">I shit you not merge netu in masina ai nebuna</mark>

![[Pasted image 20261018190408.png]]


Pingurile merg si intre noduri deci i suppose ca nu mai facem o alat ainterfata in vmware. Tine minte totusi sa dai enable la promiscous mode dupa restart/shutdown.

![[Pasted image 20261018193011.png|700]]

**In your project, add 2 machines that are connected to a network ( Cloud0 ), giving them internet access. Start them and verify connectivity to the Internet and from one to the other.**

Done see previous step

**Start an nginx server. curl it from the other machine.** **What can you do with nginx ?**

Mai intai treb instalat eu am instalat pe Linux 1
https://ubuntu.com/tutorials/install-and-configure-nginx#2-installing-nginx

Nginx e un revrese proxy dar e si 
nginx ("_engine x_") is an HTTP web server, reverse proxy, content cache, load balancer, TCP/UDP proxy server, and mail proxy server. Originally written by [Igor Sysoev](http://sysoev.ru/en/) and distributed under the [2-clause BSD License](https://nginx.org/LICENSE).


O sa fie foarte amuzant daca dai direct comanda de install pentru ca o sa esueze. De ce? Webmin asta vine cu apache2 instalat si el foloseste deja port 80 si are enable adica porneste automat daemonul deci si servciul la boot.  Fiindca nu pot 2 servicii sa calareasca acelasi port nginx se supara si dpkg e confuz si zice ca ar fi eroare de instalare dar nu e asa. 

Nginx e instalat. Opresti apache cu
```bash
systemctl stop apache2
systemctl disable apache2
# o sa dea eroare

# poti porni nginx nu e problema
systemctl start nginx
systemctl status nginx
# active running cai verzi pe pereti

# ca sa poti repara broken install si sa poti trage upgradeuri
apt install -f
```

Pornesti nodul 2 si dai 

```bash
curl http://172.16.135.129

# o sa iti dea pagina de apache
# pt ca cand ia instalat nginx el nu a suprascris index.html original
# ca sa rezolvi
# din masina cu nginx
root@ubuntu:~# cd /var/www/html/
root@ubuntu:/var/www/html# ls
index.html  index.nginx-debian.html
root@ubuntu:/var/www/html# ls -l
total 16
-rw-r--r-- 1 root root 11321 Apr  4  2018 index.html
-rw-r--r-- 1 root root   612 Oct 19 16:37 index.nginx-debian.html
root@ubuntu:/var/www/html# mv index.html index-apache.html
root@ubuntu:/var/www/html# mv index.nginx-debian.html index.html

# daca vrei sa vezi ce serviciu raspunde
curl -I http://172.16.135.129
```


 **Install and start a basic Flask server that returns a simple print statement on GET of / . curl it from the other machine.**

Instalarea o sa doara. Literalyy. Python e foarte avansat si nu mai e compatibil cu porcariile din ubuntu vechi

```bash
apt-get update
apt-get install -y python3 python3-pip python3-flask
python3 --version
pip3 --version
python3 -c "import flask; print(flask.__version__)"
```

NU INSTALA NIMIC CU PIP PENTRU CA NU SUNT PACHETE COMPATIBILE CU PYTHON PENTRU UBUNTU 16.04
INSTALEAZA TOTUL CU PYTHON SI ATAT.

>[!DANGER] 
>După ce ai rulat aceste comenzi, **nu da niciodată `pip3 install --upgrade pip`**! Versiunile noi de `pip` sunt incompatibile cu Python 3.5 și vor strica mediul de lucru.

Ne ducem pe documentatia oficiala flask si copy paste la amarata aia de app.py

```python
from flask import Flask
app = Flask(__name__)

@app.route("/")
def home():
    return "Hello from Flask!"

app.run(host="0.0.0.0", port=5000)
```

Trebuie neaparat adresa aia si faci run cu

```bash
python3 app.py 
```

De pe cealalata masina

```bash
curl http://172.16.135.129:5000
# trb sa apara hello
```

![[Pasted image 20261019180437.png]]

**SSH from one machine to the other.**

![[Pasted image 20261019180518.png]]


**Start an FTP server (hint: docker)**

Instalare docker: https://www.digitalocean.com/community/tutorials/how-to-install-and-use-docker-on-ubuntu-16-04

FTP este un protocol de transfer de fisiere intre doua masini. Se cere autentificare cu user si parola. Ideea e ca trb instalat un server ftp ca imagine de docker. Cel mai ok cred ca ar fi vsftp: https://security.appspot.com/vsftpd.html

si imaginea: https://hub.docker.com/r/garethflowers/ftp-server

Pe masina Linux 1:

```bash
# public ip ramane pe default pe  0.0.0.0
# dar nu il setez oricum
# o sa mergem fara optiunea d evolume pentru ca 
# nu e necesar sa salvam cacaturile transferate pe local
# volume specific ao cale la care vrei sa salvezi fisierele adui aminte de la epam
# daca nu pui nimic ele raman in container dar se sterg daca il stergi
docker run \
	--detach \ # in fundal
	--network host #bruh?
	--env FTP_PASS=test \
	--env FTP_USER=test \
	--name ftp-server-1 \
	garethflowers/ftp-server
# e gresita comanda data de claude e prost
# trebuie ip in primul rand il pui pe ce; al masinii
# bc its a damn server
docker run --detach --env FTP_PASS=test --env FTP_USER=test --env PUBLIC_IP=172.16.135.129 --name ftp-server-1 garethflowers/ftp-server

docker ps
# daca nu e healthy docker logs <nume container>
```

De pe cealalta masina am facut asa

```bash
apt install ftp
ftp 172.16.135.129
```

De ce e gresit ?
![[Pasted image 20261019185444.png]]

Se conecteaza la serverul gresit. 
Ceea ce inseamna ca mai exista un server de ftp deja instalat pe masinile astea gretoase
Trebui oprit pe masina Lnux 1 adica unde am serverul ftp cu docker

```bash
systemctl stop proftpd && systemctl disable proftpd
# imi da connection refused wtf
netstat -tulpn | grep 21
root@ubuntu:~# docker restart ftp-server-1 -
--help  -t      --time  
root@ubuntu:~# docker restart ftp-server-1
```

Ba da proasta ma  facut mama. Trb mapate porturile coaie

```bash
# asta nu aparea inainte si acuma e bine!
root@ubuntu:~# netstat -tulpn | grep 21
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      25574/docker-proxy
tcp6       0      0 :::21                   :::*                    LISTEN      25579/docker-proxy

# deci asta e comanda
docker run --detach --env FTP_PASS=test --env FTP_USER=test --env PUBLIC_IP=172.16.135.129 --publish 20-21:20-21/tcp --publish 40000-40009:40000-40009/tcp --name ftp-server-1 garethflowers/ftp-server
```

![[Pasted image 20261019190535.png]]


**On one machine, change the DNS provider to 8.8.8.8 .**

Asta de la uso din anu 1 

```bash
cat /etc/resolv.conf
# o sa zica sa nu modific bla bla
# o sa modific temporar
echo "nameserver 8.8.8.8" > /etc/resolv.conf
```

>[!Danger]
>**CUM INCHIZI TOPOLOGIA IN SIGURANTA?**
>Pas 1:
>Mai intai inchizi nodurile cu `poweroff`
>Pas2:
>In bara din stanga dai `Close Lab`
>Pas4:
>Te intoarce in meniul de admin. Da sign out
>Pas5:
>Inchizi vm-ul eve. Din terminalul negru poweroff

That's it.