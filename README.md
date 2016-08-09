项目说明：

本项目使用Java语言，并使用了Twilio API。使用maven来进行项目管理，集成开发环境为Eclipse。

本项目是用来通过发送短信的方式获取公交时刻表信息，根据用户的指令，将会产生不同的回复信息，具体指令如下：

   1. 发送 1，回复目前所拥有的公交路线
   2. 发送 2，回复目前所有的车站
   3. 发送 1+路线号，回复该路线的时刻表（如发送1375得到375路车的时刻表）
   4. 发送 2+车站名，回复该车站的时刻表（如发送2AA得到AA车站的时刻表）
   5. 发送 路线号+车站名+时间，回复具体的时刻表信息（如发送3AA1000，得到3路车10:00到达AA车站这一班车的详细信息）
   6. 发送其他消息将会得到错误信息和帮助提示

运行该项目所需条件:

   1. 具有Java及Java Web开发环境;
   2. 具有twilio-java-sdk(http://search.maven.org/#browse%7C-1416163511)和mysql-connector-java(如果你不使用maven或是grandle，则必须手工导入jar包)
   3. 拥有Twilio账号和能够收发短信的Twilio号码（注册新的Twilio账户之后附送免费试用时间，大家可以试试）
   4. 拥有能被外网访问的web服务器（测试可以使用ngrok，很方便）
   5. 具有MySQL数据库

如何运行：

   1. 导入schedules.sql到MySQL中；
   2. 在你的web服务器上运行com.mytwilio.servlet.ScheduleServlet并将你的公有地址复制到你的twilio 账号的messaging request url一栏中
   3. 根据我上面所写的发送信息即可
   
备注:

   1. 准备添加更多功能，准备使用Spring Struts2和Hibernate框架重构代码
   2. 我的第一个Twilio 账户试用期过了
   3. 为啥一个Twilio 号码不能同时用于语音和短信功能，我得老是切来切去，我的钱估计就这么花没了。

This is a Java app with Twilio API and using maven to manage. 
The purpose of this app is to get the bus schedule by sending a sms to a specific Twilio phone number. Depends on user's instruction, generate a corresponding response message and text back to the user:
  1. If the user text "1", reply which routes we have; 
  2. If the user text "2", reply which stops we have; 
  3. If the user text "1+route", reply the schedule of this route(e.g. 13 is for route 3); 
  4. If the user text "2+stop", reply the schedule of this stop(e.g. 2A is for stop A); 
  5. If the user text "route+stop+time", reply the specific schedule of this line(e.g. 3D1000 is for route 3 arrive at stop D at 10:00); 
  6. If the user text anything else, reply an error message and a direction.
	
To make this app work, you need: 
  1. Have a Java development environment with a Web server capable of running Java servlets;
  2. Have dependencis include twilio-java-sdk(http://search.maven.org/#browse%7C-1416163511) and mysql-connector-java( if you do not use maven or grandle, add these jars manually)
  3. Have a Twilio account and a Twilio phone number which can send and receive sms;
  4. Have a web server exposed on the Internet;
  5. Have a MySQL database running on your computer;

To run this app:
 1. schedules.sql is the sql script which can create a MySQL table and insert data;
 2. run com.mytwilio.servlet.ScheduleServlet.java on your web server and copy your public of this servlet into your twilio number's messaging request url.
 3. Text your twilio phone number according the rules I wrote above.
 
ps: 
 1. I'm working on more functions and for more complexed databases, planning to use Spring and Hibernate framework.
 2. My first Twilio Account is currently suspended due to a lack of funds :(
 3. Why I can't find a twilio number can both do voice and messaging work? I have to release and buy a new one and repeat this work. I think that's the main reason my account get suspended.


