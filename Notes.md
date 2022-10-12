 

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

##  Mongo DB
 Sql vs MongoDB 数据库    
 database vs database 数据库表/集合    
 table vs collection 数据记录行/文档    
 row vs document 数据字段    
 column vs field 索引    
 table joins vs 表连接    
 primary key vs primary key 主键 MongoDB自动将——id字段设置为主键
     
         
    
        
        MangoDB中储存的文档必须有一个_id键，这个键的值可以是任何类型的，默认是个Objectid对象。
        object中保存了创建的时间戳，所以不需要单独保存时间戳，直接通过git TimeStamp函数来获取创建时间
 
 BQ： Mongo vs MySQL？ why？   
    - Flexilbe fixed schema: adapt quick to fast changing feature requirement. 
    Schema 不固定，可以随时加减改。   
    - High Availability and easier/Simpler Horizontal Scaling/Sharding solution.  

### 结论： SQL比NON-SQL运行快，但是写入麻烦

# Distributed Object Storage & its RESTful APIs
    类似分布式的HashMap
    Total Object that can storage are Unlimited （in Amazon S3 object can storage from 0b to 5 TB.
    1. Partitioning 2. Pelication 3.Fault tolerance 4. Elastic scalabity
       1. Distribute data into different nodes
       2. Replicate same data across multiple cluster nodes
       3. If 1 server is down, can we retain data
       4. Enable more storage space if needed