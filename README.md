# Teknologi Open Source dan Terbaru
Github untuk matakuliah TOST

##Dibuat oleh:

| Type 		    | Contributor                                 |
| ------------- |:-------------------------------------------:| 
| GitHub        | // 5213100072  / Mochammad Rizki Wicaksono  | 
| ODK Learning  | // 5213100072  / Mochammad Rizki Wicaksono  | 
| 			    | // 5213100176  / Octgi Ristya Perdana       | 

###Pengertian ODK

>Open Data Kit (ODK) is a free and open-source set of tools which help organizations author, field, and manage mobile data collection solutions. 

>*Note: Berikut adalah panduan dari ODK*

> Type Form adalah **Surat Ijin Tidak Masuk**

###Prerequisite
1. Java JDK
2. Apache Tomcat 6.00 or 7.00
3. MySQL 5.3+ or MariaDB

###Installation

1. Download **ODK Aggregate Installer**.
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
