 
 Computer system


1. Start


2. Disk (ssd, hdd)
    load Data + program


3. Disk --> Memory
    Load to run(run time)


4. Load System (OS: Mac, Win, Linux) + (Manage HardWare) (Software resource)


5. Run App


6. Memory ---> CPU
    Execute machine instruction  


7. CPU --> Memory
    Return computed result


8. DataBase SQL/NoSQL
    Create, read, update, delete(CRUD)
        All this is Cached data


总结： Disk 存储  Memory 读写 CPU 运行


9. Memory ---> Disk
    Cached data saved to storage.


10. Disk ---> Memory
    Take the saved Data(Cache data), back to system


总结： Cached data（缓存）这个概念不只是内存->硬盘，也可以是硬盘->服务器，等。
        只要是能通过储存在更快的地方加速程序运行的，都可以被称为缓存 数据。
        许多软件会在本地缓存图片等，所以即使断网也会加载出部分图片。
   
---------------------------------------------------------------------------
---------------------------------------------------------------------------
Internet


1. 3 way hand Shake(三次握手)
    Use hand Shake to create a safe, stable and correct connection between the local machine and the host.


2. Local --> Host (send request)
    Host (receive request)
    Host --> Local (send Respond)
    Host (receive respond)
    (HTTP 基础协议模型)
    All these Use HTTP


3. HTML, CSS, JS(前端-图像界面)
    Server， service... (后端，数据库等)


4. EX：
    when user click the button,
    The user's local server send a HTTP request to Amazon's server


        Structure of HTTP Request


        HTTP Method: POST, GET, PUT, DELETE
            Post: www.amazon.com/signup (URL)


        Request Header:
            Host: www.amazon.com
            Path: /signup
            Accept: text/html
            Content-length: 22
            Cookie: session_id=939asdasgjsajaskf


        Request Body: 描述request本身的东西。例如request的密码，用户名等。·
            name=xxx&email=xxx@xx&password=xxx&ALLOTHERS


-------------------------------------------------------------------------
-------------------------------------------------------------------------
Structure of HTTP Response
1. Start Line:
    Status code:
    200 OK; 404 Not found; 400BadRequest; 500 Server ERROR;


    HTTP/1.1.200 OK


2. Response Header: Meta-data


    Date:01 Dec 019 23:121:23
    Content-Type: type/html
    Content-Lneght: 122
    Set-Cookie: session-1d:xxxxxxxxxx; Expires = 30Dec 2019 23:54:21


3.  Response Body:
    Contains data content:


    <html>
    <Head>
        <title>xxxx<title>
    </head>
    <body>
            XXXXXXXXXXXXXXXXXXX
        XXXXXXXXX.
    </body>
    </html>


-------------------------------------------------------------------------
-------------------------------------------------------------------------


Homework:


Local Client Machine:
        本地browser
Amazon Server:
    Java APP of E-Commerce port：80 （运行中）




1. Browser port: 123 ---> Send HTTP Request: Get www.amazon.com:80/ HTTP/1/1 ---> Amazon Server
    打开Amazon.com(发送 GET 请求) 读取amazon 首页的内容 ---> 获得 Amazon Server 的response  
        HTTP请求会转换：
                HTTP 请求会变成 TCP 的数据包（01010011的形式）
                TCP数据包通过IP找到amazon服务器对应的ip地址
                    所有的上述数据都是通过NetWOrking 物理的方式进行传递
                具体步骤就是 HTTP-> TCP -> IP-> Networking -> IP -> TCP -> HTTP 复原
       
        Amazon服务器的 E-Commerce 是运行的 HTTP， 所以上述通过networking 之后需要转换回http
        处理完HTTP之后 会返回Response(HTTP) 返回过程和上述发送一样


        Local Browser 收到 Response 之后会 render HTTP to 人可以看懂的画面(Graph User Interface)
             
    前端编程语言：
        HTML 负责 具体 content：文字 图片 等
        CSS 负责style： 文字字体，大小 格式
        JavaScript： Action、 FUnction： 例如 弹出动作 控制动画


----------------------------------------------------------------------------
----------------------------------------------------------------------------
What is JSON:
    JavaScript Object Notation
        JSON 是一种数据格式（文本格式） 用于存储和传输数据
        是name value pair 或 key value pair
            EX：
                {
                id: 01,
                name: ryan,
                age: 20,
                }


                {
                id: 02,
                name: gin,
                age: 25,
                }
                total: 2
        Data is separated by commas
        所有名字都要有 “”；
------------------------------------------------------------------------------------
------------------------------------------------------------------------------------


API Application programming interface
    API of a system is a set of Rules that define operation on data of that system
        需要一个系统（通常是网站）              CRUD 操作（对系统数据）
   
    Developers build the system, and also build API for user to use/call without knowing internal details.


    API usually follow standard or style for user friendly/ better communication.
            FOCUS ON REST-Ful API
                要学会读写：
                    都懂别人的api
                    写自己使用的api


                要看 Responds Code， 不同含义
                如果自己开发app，需要调取（如 yelp的酒店数据） 就要使用yelp的api
                通过call yelp的api， 可以在自己的app上调取数据或软件


                API 无处不在。
                以上的例子都是Rest api


        1. REST 是一种标准
            是一种风格 designing for web/HTTP service
       
        2. USE proper HTTP methods for CRUD purpose on the data of the service


        3. Data 是以 JSON的format 表达和传输（JSON是主流， 但是有别的方式）


        4. 如果返回的是大量的数据， 可以use query string parameter after URL filter results。
            假设USER-1 有10000条返回的数据， 可以只拿其中几条。




------------------------------------------------------------------------------------------------
------------------------------------------------------------------------------------------------
##     JAVA


        Java --> 第三方工具(tomcat， maven)等 ----> 诞生了Spring Core -----> spring 子框架 (Spring MVC， Spring DATA， Spring security， many others.....) ------> Spring Boot-----> Spring cloud
                                                        Conatiner， Bean， Context for loC、 Dependcy Injection                          Easy to create stand-alone project.   Framework to build Microservice based on Spring boot


        Spring概括：
            Spring is a java framework for building application with POJO Using DI/IOC container
                FrameWOrk: a collection of pre-written code where to add your own code to build application.
                    使用别人写好的模板，我们再加入自己的代码。 使用的是别人的框架，所以要follow 规定


                POJO： Plain Old Java Object 每天写的code， Nothing special。 不需要使用别的语言。


                DI/IOC
                Dependency Injection/ Inversion of control（非常抽象）


        MVC Design pattern： Model view controller
            用户看的到的就是前端
            用户看不到的就是后端


            MVC： 设计一个web的后端


            三个OBjective层次：
                Client ----> Controller
                    Request: Get/users/1
                        用户向controller 发出一个request， 由controller 接住
                Controller ----> Model
                    Access/ modify（CALl）调用
                        Controller回去call model层
                    Model 分为两层
                        DVO： Data value Object/ Domain / 代表数据的value 例如： User
                        DAO： Data Access Object / UserDao/ DAO 用于管理DVO的数据


                    Model层的DAO 回去call -----> database的数据
                    Database 数据库返回数据
                Model ----> 数据返回给 controller（从database 提取出来的）
                controller 再把数据传给前端的View层
                View 层再把数据返回给 Client


----------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------
            MongoDB:
                JSON-like Document DB with JSON-like Query
                    MongoDB is a source-available cross-platform document-oriented database program
                    Classified as a NoSQL database program, MongoDB uses JSON-like documents with optional schemas
                    用mongo 存Non critical data
           
            SQL database: JSON  vs NONE SQL database: MongoDB
                Mongo support unstructured data // SQL does not support that.
            MongoDB里可以修改某一个doc里面的某一项数据，可以在一个doc里添加新的条件（在sql里无法实现）


            BSON:
                It is a binary encoded of JSON-Like Doc, that mango DB uses when storing documents in collections.
                It add support for data types like Data nad binary that aren't supported in JSON.


            Sharding:
                splotes large dataset into smaller data set.
                    当数据过大，  需要确保稳定性时，使用多台服务器存储数据，使用sharding可以分流数据
                    mongoDB 对sharding 使用更加方便


----------------------------------------------------------------------------------------
----------------------------------------------------------------------------------------

Microservice of Data pipline system
    A microservice pipeline uses a microservice origin to listen for or read JSON-formatted requests.
        In the pipeline, you can use any available processor to transform and route the records as needed. 
        You can also use destinations and executors to write data and execute additional actions as needed.
        Then, use one or more microservice destinations to send responses back to the origin and write the records to a destination system if necessary.
        The origin then transmits JSON-formatted responses back to the origin system.

        EX:
            you might use the WebSocket Server origin to listen at a WebSocket endpoint and process all authorized requests.
            In the pipeline, you use stages to process the data and route records to different destinations based on whether the record is considered a success record or bad request record
            You use two Send Response to Origin destinations to return different responses, 200 for OK and 400 for Bad Request.
            The origin then passes the records with the responses back to the WebSocket endpoint.

            Microservice origins listen for or read JSON-formatted requests. They also send responses from microservice destinations back to the origin system.

                use the following origins in microservice pipelines:
                    REST Service origin - Listens on an HTTP endpoint, parses the contents of all authorized requests, and sends responses back to the originating REST API. Creates multiple threads to enable parallel processing in a    multithreaded pipeline.

                    WebSocket Client origin - Reads data from a WebSocket server endpoint. Can send responses back to the origin system as part of a microservice pipeline.
                    
                    WebSocket Server origin - Listens on a WebSocket endpoint and processes the contents of all authorized WebSocket client requests. Creates multiple threads to enable parallel processing in a multithreaded pipeline. 
                    
                    Can send responses back to the origin system as part of a microservice pipeline.


    WebSocket 
        websocket is a computer communication standard protocol, provding full deplex communication channel ocer a single TCP connection
        Since communication is 2-way, so server can initiate and push real time data to client side.

        HTTP:
            Client --> request --> Server
            Server --> respond --> Client

        WebSocket:
            Client --> handshake --> Server
            Server --> Acknowledgement --> client

            Client <----- Bi directional messages------> Server

            Client <-- end connection --> Server

------------------------------------------------------------------------
------------------------------------------------------------------------


### TCP -three way HandShake (need response to build connection) 200ms
Slow but reliable transfers   
Email, web browsing

    Sender                          Receiver
    Send SYN ---------------------> Receive SYN
    Receive ACT <------------------ Return SYN ACK
    Send Application Data --------> Receive Data

### UDP  (Just send anything, no need to check) 100ms
Fast but Non guaranteed transfers
VoIP
Music Streaming

    Sender                          Receiver
    Receive Request <-------------- Send Request
    Respond ----------------------> Receive Respond
    Respond ----------------------> Receive Respond
    Respond ----------------------> Receive Respond

### TCP- 4 Wat HandShake (Same from 3 way but with end) 

### UDP-QUIC 0ms

    Sender                          Receiver
    Send -------------------------> Receive

## Project connections    
    
    Client -> Media service
            -> New service 
             -> Analytic service -> Notification service

### Network connection - Layers

    Network Connections View
     Host A -> Router -> Router -> Host B

     TCP/IP Model
     Application -> transport -> Network -> Network Access and return








