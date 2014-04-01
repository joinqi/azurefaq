# 云服务

#### 能否使用自己的 DNS 地址?
>可以在域名提供商中配置CNAME指定到*.chinacloudapp.cn域名下

#### 中国版Azure PublishSetting 文件下载
>由于中国版与国际版Azure的服务端点有所不同，所以在中国版Azure上需要使用Publish Setting文件时请从以下URL下载：[https://manage.windowsazure.cn/publishsettings/index](<https://manage.windowsazure.cn/publishsettings/index>)

#### 中国版与国际版Azure端点映射
><table>
<tbody>
    <tr>
        <th>服务类型</th>
        <th>国际版URI</th>
        <th>中国版URI</th>
    </tr>
    <tr>
        <td>Windows Azure常规</td>
        <td>*.windows.net</td>
        <td>*.chinacloudapi.cn</td>
    </tr>
    <tr>
        <td>Windws Azure计算</td>
        <td>*.cloudapp.net</td>
        <td>*.chinacloudapp.cn</td>
    </tr>
    <tr>
        <td>Windows Azure存储</td>
        <td>*.blob.core.windows.net<br>
        *.queue.core.windows.net<br>
        *.table.core.windows.net</td>
        <td>*.blob.core.chinacloudapi.cn<br>
        *.queue.core.chinacloudapi.cn<br>
        *.table.core.chinacloudapi.cn</td>
    </tr>
    <tr>
        <td>Windows Azure服务管理</td>
        <td>https://management.core.windows.net</td>
        <td>https://management.core.windows.net</td>
    </tr>
    <tr>
        <td>SQL 数据库</td>
        <td>*.database.windows.net</td>
        <td>*.database.chinacloudapi.cn</td>
    </tr>
    <tr>
        <td>Windows Azure 管理门户</td>
        <td>http://manage.windowsazure.com</td>
        <td>http://manage.windowsazure.cn</td>
    </tr>
    <tr>
        <td>SQL Azure 数据库管理 API</td>
        <td>https://management.database.windows.net</td>
        <td>https://management.database..chinacloudapi.cn</td>
    </tr>
    <tr>
        <td>服务总线</td>
        <td>*.servicebus.windows.net</td>
        <td>*.servicebus.chinacloudapi.cn</td>
    </tr>
    <tr>
        <td>ACS</td>
        <td>*.accesscontrol.windows.net </td>
        <td>*.accesscontrol.chinacloudapi.cn</td>
    </tr>
    <tr>
        <td>SQL 数据库导入/导出服务映射端点</td>
        <td>1.中国东部：https://sh1prod-dacsvc.chinacloudapp.cn/dacwebservice.svc<br>2.中国北部：https://bj1prod-dacsvc.chinacloudapp.cn/dacwebservice.svc</td>
        <td></td>
    </tr>
</tbody>
</table>


####VS2012发布遇到无法上传的问题
>当使用VS工具发布Cloud Service时，需要注意当前Cloud Service绑定的Subscription必须存在。VS会保存一个Subscription的profile，当你删除这个Subscription而没有更新profile，你就会发现那个删除的Subscription仍然能被勾选。如果你选了这个Subscription去发布，发布虽能成功，但是在管理界面下查看，实际你的Cloud Service是绑定的一个当前存在的Subscription而不是VS里勾选的那个删除的Subscription。
注：将错就错，当你已经用删除的Subscription发布了一个Cloud Service，而且想把它更新成https的访问形式，那么原来Subscription所需的证书都需要上传，不然更新发布会出错。不建议使用这种方法去发布！

>如果你发布cloud service时，勾选了允许远程登入，那么VS会自动的给你创建一个证书在你本机的personal下。并会在你的ServiceConfiguration.Cloud.cscfg下自动添加如下代码：
``` xml
<Certificate name="Microsoft.WindowsAzure.Plugins.RemoteAccess.PasswordEncryption" 
thumbprint="**********************************" thumbprintAlgorithm="sha1" />
```
当你需要把这个Cloud Service发布成https的形式时，你需要把这个证书也上传到cloud service的证书里。

[返回首页](</index.md>)
