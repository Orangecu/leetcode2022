

## What happens when we hit www.amazon.com (IP) in browser
1. when we type www.amazon.com in browser, browswe will auto-complete based on history.\
2. The browser check cache for a DNS record to find the IP address for amazon,com, browser -> os ->ISP(internet service provider) 
3. If URL is nor in rhw cache, Browser will initiate a DNS (Domain Name Service) query to find the IP ADDRESS of a server hosting amazon.com.
4. Once browser receives the IP address, will establish a TCP connection with Amazon servier using 3-way Handshake.
5. Browswe will send GET request to Amazon server to get the index web page, (and pass cookies to request header ), if not first time.
6. The server handles the request and sends back a http response,(index web page), also containing addition information in header like cookies to set.
7. The browser will parse the HTML content sending GET request for additional resource such as images, JS, CSS, these static files are also cahes by the browser, the render the final GUI.

## What is JSON 
1. Json is light weight format for storing and transfer data
2. Data is in name/Value pairs
3. Data is sparates by commans


## Whag is API (Application Rogramming Interface)
1. API of a System is set of rule that define operaction on data of that system.(增删改查)


## Rest API 
1. Standerd style for disigning API of web//http servive
# REST-FUL

# Spring
1. container, Bean, Context for Ioc
2. pre written code , to add own code 
3. need to follow the struction/patten/style 
4. POJO: NORMAL JAVA    
## Spring mvc for web develoment
## Spring data for database integration
## Spring Security for Authentiction
## Spring Boot
1. java annotation for Spring Boot function

## Spring Cloud

## MVC
1. model view controller
2. client request GET to Controller
3. Ccontroller will access/modify Model(data value object/data access object)(dvo dao)
4. 