# Maven接入阿里云仓库

* Maven安装目录/conf/settins.xml
* mirrors
*   ```text
  <mirrors>
      <mirror>
          <id>alimaven</id>
          <name>aliyun maven</name>
          <url>http://maven.aliyun.com/nexus/content/repositories/central</url>
          <mirrorOf>central</mirrorOf>        
      </mirror>
  </mirrors>
  ```

