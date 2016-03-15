# Teknologi Open Source dan Terbaru
Github untuk matakuliah TOST

*Note: Berikut adalah panduan dari ODK*

##Dibuat oleh:

Github        :   5213100072   Mochammad Rizki Wicaksono

ODK Praktikum :   5213100072   Mochammad Rizki Wicaksono
                  5213100176   Octgi Ristya Perdana

###Pengertian ODK

Open Data Kit (ODK) is a free and open-source set of tools which help organizations author, field, and manage mobile data collection solutions. 

###Installation

1. Download **ODK Aggregate Installer**.
2. Install dengan mengikuti petunjuk yang ada di Installer.
3. Kemudian buka Readme.html yang ada dalam folder tujuan *Installer*
4. Masukan syntax yang berada pada file *create_db_and_user.sql* kedalam database yang digunakan.
5. Copy file *ODKAggregate.war* pada folder instalasi ke dalam *webapps* di *tomcat*
6. Folder baru dalam webapps akan dibuat otomatis sama dengan isi *ODKAggregate.war*
7. Masukan database connect .jar kedalam folder lib di dalam tomcat servernya, dalam kasus ini *mysql-connector-java-5.1.38.jar*