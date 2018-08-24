## What is Cors and How its to be enable in between to different servers
Know I am discussing with how to enable Cors between Tomcat and Angular 6 using REST API

Generally, we can't access the data between two servers. If we want to access 
the data we should enable Cros.
Cros is acting as a gateway to access data.
Now I will show how to enable cross in Tomcat and angular 6

## Tomcat:
For enabling cors we have to add below few lines of code in server **web.xml**
```
<filter>
  <filter-name>CorsFilter</filter-name>
  <filter-class>org.apache.catalina.filters.CorsFilter</filter-class>
</filter>
<filter-mapping>
  <filter-name>CorsFilter</filter-name>
  <url-pattern>/*</url-pattern>
</filter-mapping>
```
In the above code, /* means it will allow all the requested servers.
If you want to allow particular URL then instead of that mention the URL name.

For more Refer Here : https://enable-cors.org/server_tomcat.html

## Angular 6:
For enabling Cors we have to create one proxy JSON file to allow the required servers for access in the project after you have to add that file path to the package.json file after ng serve sentence which means patching the proxy file along with the project. I attached the two files above have a look.

**proxy.config.json**
```
 {
    "/path":{
        "target":"http://localhost:9090/ProjectName/",
        "secure":false,
        "logLevel":"debug",
        "changeOrigin":true
    }
}
```
**package.json** add this 
```
"start": "ng serve --proxy--config proxy.config.json"  
```
