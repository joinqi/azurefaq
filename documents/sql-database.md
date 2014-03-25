# SQL Database

#### 使用SQL Database的限制
>SQL Database现在已知有如下限制、不支持分布式查询、不支持.NET CLR类型、不支持数据备份和恢复、需要每个表都有聚集索引。SQL Database提供两种不同类型的服务：web和business。web类型数据库最大尺寸为5GB，Business类型数据库最大尺寸为150GB。如果数据库超出了这个限制，需要使用数据分片功能将数据分布到多个SQL Database数据库上。

#### SQL Database 的数据库容量最大是多少
>SQL Database数据库分为Web版和Business版，两者的区别是Web版有两个容量大小选项，1GB和5GB。Business版有7个容量可供选择（10GB，20GB，30GB，40GB，50GB，100GB，150GB）

#### SQL Database 怎么收费
>SQL Database按照使用量收费，一般情况是用多少，就收多少。
计费方式上有两个地方需要注意
<ul>
<li>如果实际存储使用了2.3GB，将向上舍人到3GB收费</li>
<li>具体收费有一个起始用量的概念，用量是按照DU来计算，比如数据库现在有60GB的数据，前50个GB需要12.6个DU的费用，后面的10GB按照0.1DU/GB收费,，国际版一个DU是$9.99,所以总费用是(12.6+10X0.1)X$9.99=$135.864,Mooncake官方报价没有出来，但收费策略应该是一样的，只是DU的价格会不一样.[SQL Database国际版收费策略](http://www.windowsazure.com/zh-cn/pricing/faq/sql-database-how-do-database-charges-appear-on-bill/)参考如下<table> <tbody> <tr><th>数据库大小</th><th>数据库单位<br>(每个 DU = $9.99)</th></tr> <tr> <td>0 到 100 MB</td> <td>0.5 DU</td> </tr> <tr> <td>100 MB 到 1 GB</td> <td>1 DU</td> </tr> <tr> <td>1 GB 到 10 GB</td> <td>第一个 GB 为 1 DU，<br>每个额外的 GB 为 0.4 DU</td> </tr> <tr> <td>10 GB 到 50 GB</td> <td>前 10 个 GB 为 4.6 DU，<br>每个额外的 GB 为 0.2 DU</td> </tr> <tr> <td>50 GB 到 150 GB</td> <td>前 50 个 GB 为 12.6 DU，<br>每个额外的 GB 为 0.1 DU</td> </tr> </tbody> </table></li><ul>

#### SQL Database如何同本地SQL Server做数据同步
>[TODO]

#### 在Windows Azure虚拟机上配置SQL Server 2012 AlwaysOn
>在IssS层面上，如果需要SQL Server的高可用，可以通过配置虚拟机中安装的SQL Server来实现。对于SQL Server 2008来说可以通过镜像的方式来实现HA。对于SQL Server 2012来说可以通过新添加的SQL Server AlwaysOn功能获得HA。SQL Server AlwaysOn功能可以通过下述几篇文章来学习配置。
>[Step-By-Step: Creating a SQL Server 2012 AlwaysOn Availability Group](http://blogs.technet.com/b/canitpro/archive/2013/08/20/step-by-step-creating-a-sql-server-2012-alwayson-availability-group.aspx)
>[Tutorial: AlwaysOn Availability Groups in Windows Azure (PowerShell)](http://msdn.microsoft.com/en-us/library/windowsazure/jj870963.aspx)
>[High Availability and Disaster Recovery for SQL Server in Windows Azure Virtual Machines](http://msdn.microsoft.com/en-us/library/jj870962.aspx)

#### Windows Azure SQL Database防火墙
>在默认情况下，SQL Database数据库不允许从任何IP地址的链接。用户必须手动指定从哪些IP地址可以访问SQL Database。可以从SQL Database数据库的仪表板界面单击“管理允许的IP地址”来管理允许访问的IP地址。另外，“允许的服务”选项应该设置成“是”。这个选项允许用户所部署的云服务能访问这个数据库，无论他们的IP地址是什么。

[返回首页](</index.md>)