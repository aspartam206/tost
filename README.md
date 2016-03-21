# Teknologi Open Source dan Terbaru
Github untuk matakuliah TOST

##Dibuat oleh:

| Type 	        | Contributor                                 |
| ------------- |:-------------------------------------------:| 
| GitHub        | // 5213100072  / Mochammad Rizki Wicaksono  | 
| ODK Learning  | // 5213100072  / Mochammad Rizki Wicaksono  | 
|               | // 5213100176  / Octgi Ristya Perdana       | 

##Folder Structure
|--[README.md](//github.com/aspartam206/tost/blob/master/README.md)

|--[LICENSE](//github.com/aspartam206/tost/blob/master/LICENSE)

|--form

>|--[form.xml](//github.com/aspartam206/tost/blob/master/form/form.xml)

|--doc

>|--[form.odf](//github.com/aspartam206/tost/blob/master/doc/form.odf)

>|--[letter.odf](//github.com/aspartam206/tost/blob/master/doc/letter.odf)

###Pengertian ODK

>Open Data Kit (ODK) is a free and open-source set of tools which help organizations author, field, and manage mobile data collection solutions. 

>*Note: Berikut adalah panduan dari hasil praktikum ODK*

> Type Form adalah **Surat Ijin Tidak Masuk**

###Prerequisite
1. Java JDK
2. Apache Tomcat 6.00 or 7.00
3. MySQL 5.3+ or MariaDB

###Installation

1. Download [**ODK Aggregate Installer**](//opendatakit.org/downloads/).
2. Install dengan mengikuti petunjuk yang ada di Installer.
3. Kemudian buka Readme.html yang ada dalam folder tujuan *Installer*
4. Masukan syntax yang berada pada file *create_db_and_user.sql* kedalam database yang digunakan.
5. Copy file *ODKAggregate.war* pada folder instalasi ke dalam *webapps* di *tomcat*
6. Folder baru dalam webapps akan dibuat otomatis sama dengan isi *ODKAggregate.war*
7. Masukan database connect .jar kedalam folder lib di dalam tomcat servernya, dalam kasus ini *mysql-connector-java-5.1.38.jar*
8. Coba masuk kedalam alamat host tomcat server ODK. example: //localhost:8080/ODKAggregate/
 
###Apache Tomcat 7 Additional Step

1. Edit "context.xml" (under Tomcat 7's conf directory /etc/tomcat/) to have the attribute 'useHttpOnly' set to false.
	
	```XML
	<Context useHttpOnly="false">
		<!-- Default set of monitored resources -->
		<WatchedResource>WEB-INF/web.xml</WatchedResource>

		<!-- Uncomment this to disable session persistence across Tomcat restarts -->
		<!--
		<Manager pathname="" />
		-->
		<!-- Uncomment this to enable Comet connection tacking (provides events
		     on session expiration as well as webapp lifecycle) -->
		<!--
		<Valve className="org.apache.catalina.valves.CometConnectionManagerValve" />
		-->
	</Context>
	```

2. Then go to /usr/share/tomcat7/webapps/WEB-INF/ Add "glassfish-web.xml" under ODK Aggregate's WEB-INF directory with the content
	
	```XML
	<?xml version="1.0" encoding="UTF-8"?>
	<glassfish-web-app>
	    <session-config>
	        <cookie-properties>
	            <property name="cookieHttpOnly" value="false" />
	        </cookie-properties>
	    </session-config>
	</glassfish-web-app>
	```

3. Add "jetty-web.xml" under ODK Aggregate's WEB-INF directory with the content
	
	```XML
	<?xml version="1.0"  encoding="ISO-8859-1"?>
	<!DOCTYPE Configure PUBLIC "-//Jetty//Configure//EN" "http://www.eclipse.org/jetty/configure.dtd">
	<Configure class="org.eclipse.jetty.webapp.WebAppContext">
	    <Get name="sessionHandler">
	        <Get name="sessionManager">
	            <Set name="secureCookies" type="boolean">true</Set>
	        </Get>
	    </Get>
	</Configure>
	```

###Create Form

1. Buat form secara online menggunakan [build.opendatakit.com](//build.opendatakit.com) 
2. Untuk contoh ada di folder from pada repo ini [form/form.xml](//github.com/aspartam206/tost/blob/master/form/form.xml)

###Upload form to ODKAggregate Server

1. Loginlah kedalam user yang dibuat pada proses installasi.
	
       *note:default password adalah aggregate.*

2. Upload pada menu *form management*.

###Collect data form ODK Connect on Android

1. masuk pada play store, dan cari ODK Connect.
2. kemudian install seperti biasa.
	
       *note:ODK Connect juga tersedia pada website [opendatakit.com](//opendatakit.com).*

3. kemudian buka applikasinya dan setting server sesuai dengan host yang disetting saat installasi.
4. masuk kemenu *Get Form*, tunggu hingga selesai, kembali ke menu utama.
5. kemudian masuk kemenu *Fill Black Form*, dan isikan data sesuai keinginan, dan kembali kemenu utama.
6. Kirim hasil form dengan menggunakan menu *Send Finalize Form*.

###Screenshot

>![alt text][sspc1]

<!--
![alt text][sshp1]
![alt text][sshp2]
![alt text][sshp3]

![alt text][sshp4]
![alt text][sshp5]
![alt text][sshp6]
-->

>![alt text][sstilehp]

[sspc1]: http://drive.google.com/uc?export=view&id=0B2xl7OulaZkwU0Uwa1pzd2R3bUU "ScreenShotPC 1"
[sstilehp]: http://drive.google.com/uc?export=view&id=0B2xl7OulaZkwMTk4ZFVoWk1DQms "ScreenShotHP Tile"
[sshp1]: http://drive.google.com/uc?export=view&id=0B2xl7OulaZkwd2dKVWxJV2FVUTAyVm1uX1M4UjIzSk5qSjc0 "ScreenShotHP 1"
[sshp2]: http://drive.google.com/uc?export=view&id=0B2xl7OulaZkwZXJkOW14SU5oTDZOYVpGeE9NTlZ3U25admFv "ScreenShotHP 2"
[sshp3]: http://drive.google.com/uc?export=view&id=0B2xl7OulaZkwaF9vUUZyN0E4eUI1QzU1R2pVekhya254NUlN "ScreenShotHP 3"
[sshp4]: http://drive.google.com/uc?export=view&id=0B2xl7OulaZkwdXgwa0xRMFNwRVNrOS1haHM3R2p5Qm5kT3BR "ScreenShotHP 4"
[sshp5]: http://drive.google.com/uc?export=view&id=0B2xl7OulaZkwZWx6b01KRXF1VS1nYlhsY1RrS3JVRG0zcm5F "ScreenShotHP 5"
[sshp6]: http://drive.google.com/uc?export=view&id=0B2xl7OulaZkwck53QlFaMGpid081RGFfa1FHbHlmOGpLTHBV "ScreenShotHP 6"