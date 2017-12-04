vagrant-haproxy-demo
====================

Ada 3 VM mini-network di dalam VirtualBox. 
3 host tersebut adalah haproxy (172.28.33.10), test (172.28.33.11), dan web2 (192.168.100.12)

| Host port | Guest machine | Guest port | Notes
------------|---------------|------------|---
| 8080 | haproxy | 8080 | HAProxy Admin Interface
| 8081 | haproxy | 80 | Load Balanced Apache

* It installs Apache on the two web servers, and configures it with a index page that identifies which host you're viewing the page on.
* It installs HAProxy on the haproxy host, and drops a configuration file in place with the two webservers pre-configured.  It doesn't require HAProxy to be the default gateway because it NAT's the source IP as well as the destination IP.

# Prerequisites
1. Install Vagrant
2. Install Virtualbox
3. Clone atau download zip file dan extract pada tempat yang kosong
4. Nyalakan virtual machine yang berisikan environment Bitnami-wordpress (opsional)

# Steps
1.  Buka Vagrantfile lalu ubah IP virtual machine yang akan dijadikan host
2.  Save Vagrantfile
2.  Buka haproxy-setup.sh lalu ubah IP server web1 dan web2 sesuai dengan IP pada virtual machine
3.  Save haproxy-setup.sh
4.  Nyalakan terminal, arahkan ke local path tempat disimpan Vagrantfile, lakukan vagrant up 
5. 	Pada terminal, tulis code berikut untuk masuk ke dalam VM test: vagrant ssh test (VM pertama)
6.  Kemudian tulis code berikut untuk menginstall apache2: sudo apt-get install apache2-utils
7.  Buka [http://localhost:8080/haproxy?stats](http://localhost:8080/haproxy?stats) di browser.
8.  Buka [http://localhost:8081/](http://localhost:8081/) di browser. Ini adalah loadbalanced interface untuk kedua website.
    Atau bisa juga dibuka dari IP haproxy : 172.28.33.10
9.  Untuk mengecek statistik pada VM test, tulis pada terminal: ab -n 1000 -c 1000 http://172.28.33.10/
10. Refresh halaman [http://localhost:8080/haproxy?stats](http://localhost:8080/haproxy?stats) untuk melihat perubahan yang signifikan

# Reference material
* github.com/justintime/vagrant-haproxy-demo

"# uas cloud" 
