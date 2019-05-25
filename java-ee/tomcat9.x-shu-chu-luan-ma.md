# Tomcat9.x输出乱码

* 来到Tomcat安装目录，进入conf目录
* 打开logging.properties文件
* 1catalina.org.apache.juli.AsyncFileHandler.encoding、2localhost.org.apache.juli.AsyncFileHandler.encoding、3manager.org.apache.juli.AsyncFileHandler.encoding、4host-manager.org.apache.juli.AsyncFileHandler.encoding、5java.util.logging.ConsoleHandler.encoding的值全部修改为系统默认编码

