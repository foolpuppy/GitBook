# Servlet 输出乱码

Servlet 中 out.print，输出到网页乱码，首先看自己浏览器的网页编码是否和你JSP 中设置的编码一样。

### 表单默认提交编码是UTF-8

1. request.setCharacterEncoding\("UTF-8"\)的作用是设置对客户端请求进行重新编码的编码。显然这个作用范围不同不可取。 

    2. response.setCharacterEncoding\("UTF-8"\)的作用是指定对服务器响应进行重新编码的编码。 这是在服务器端的编码可以选择。

   **3. response.setContentType\(MIME\)的作用是使客户端浏览器，区分不同种类的数据，并根据不同的MIME调用浏览器内不同的程序嵌入模块来处理相应的数据。\(推荐使用\)**

**例:**

```text
response.setContentType("text/html;charset=utf-8");
```

## 最后我用过滤器结合 response.setContentType\(MIME\) 实现全站编码统一

