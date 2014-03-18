# Web站点
#### 如何给自己的Web站点增加自定义MIME类型
>在Web站点的config文件中增加如下设置
>```xml
<configuration>
    <system.webServer>
        <staticContent>
            <mimeMap fileExtension=".mp4" mimeType="video/mp4" />
            <mimeMap fileExtension=".m4v" mimeType="video/m4v" />
     </staticContent>
    </system.webServer>
</configuration> 
```

[返回首页](</index.md>)