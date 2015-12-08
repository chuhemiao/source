title: curl的基本用法
id: .nan
categories:
  - PHP
date: 2015-08-25 12:39:31
tags:
---

1.  curl_init(参数1)

    1.  初始化一个新的会话，返回一个curl句柄，否则返回false

        2.  如果参数提供了，curlopt_url()选项将会被设置成这个值。可以使用curl_setopt()手动设置
2.  curl_setopt(参数1，参数2，参数3)

    1.  设置一个curl传输参数

        2.  参数1由curl_init()返回的句柄

        3.  参数2需要设置的选项，参数3对应的值（CURLOPT_URL, 'http://localhost/upload.php'）

            1.  **`CURLOPT_POSTFIELDS-`**`》全部数据使用HTTP协议中的"POST"操作来发送。要发送文件，在文件名前面加上@前缀并使用完整路径。这个参数可以通过urlencoded后的字符串类似'para1=val1&amp;para2=val2&amp;...'或使用一个以字段名为键值，字段数据为值的数组。如果value是一个数组，Content-Type头将会被设置成multipart/form-data。`
    4.  参数3的类型可以是bool，int，string，array。
3.  curl_exec(参数1)

    1.  执行一个curl会话，成功返回true，失败返回false

        2.  参数1curl_init()返回的curl句柄
4.  curl_close(参数1)

    1.  关闭一个curl会话 无返回值

        2.  参数1由curl_init()返回的curl句柄
5.  curl_getinfo(参数1，参数2)

    1.  获取一个curl链接资源句柄的信息

        2.  参数1由curl_init()返回的curl句柄

        3.  参数2**`CURLINFO_REDIRECT_TIME`** - 在事务传输开始前重定向所使用的时间    "total_time"
6.  curl_multi_getcontent(参数1)

    1.  如果CURLOPT_RETURNTRANSFER作为一个选项被设置到一个具体的句柄，那么函数将会以字符串的形式返回那个curl句柄获取的内容

        2.  参数1curl_init()返回的句柄
7.  curl_setopt()参数很多，有些自己看手册把.
8.  基本例子：// 1\. 初始化一个cURL会话
        $ch = curl_init();

            // 2\. 设置请求选项, 包括具体的url
        curl_setopt($ch, CURLOPT_URL, "http://www.360weboy.com");
        curl_setopt($ch, CURLOPT_RETURNTRANSFER, 1);
        curl_setopt($ch, CURLOPT_HEADER, 0);

            // 3\. 执行一个cURL会话并且获取相关回复
        $response = curl_exec($ch);

            // 4\. 释放cURL句柄,关闭一个cURL会话
        curl_close($ch);