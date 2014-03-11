# SQL Database

#### SQL Database 怎么的数据库容量最大是多少
>SQL Database数据库分为Web版和Business版，两者的区别是Web版有两个容量大小选项，1GB和5GB。Business版最小10GB，20GB，30GB，40GB，50GB，100GB，150GB

#### SQL Database 怎么收费
>SQL Database按照使用量收费，一般情况是用多少，就收多少。
计费方式上有两个地方需要注意
<ul>
<li>如果实际存储使用了2.3GB，将向上舍人到3GB收费</li>
<li>具体收费有一个起始用量的概念，起始用量是按照DU来衡量，具体收费策略可以参考[国际版](http://www.windowsazure.com/zh-cn/pricing/faq/sql-database-how-do-database-charges-appear-on-bill/),Mooncake官方报价没有出来，但收费策略应该是一样的<table> <tbody> <tr><th>数据库大小</th><th>数据库单位<br>（每个 DU = $9.99）</th></tr> <tr> <td>0 到 100 MB</td> <td>0.5 DU</td> </tr> <tr> <td>100 MB 到 1 GB</td> <td>1 DU</td> </tr> <tr> <td>1 GB 到 10 GB</td> <td>第一个 GB 为 1 DU，<br>每个额外的 GB 为 0.4 DU</td> </tr> <tr> <td>10 GB 到 50 GB</td> <td>前 10 个 GB 为 4.6 DU，<br>每个额外的 GB 为 0.2 DU</td> </tr> <tr> <td>50 GB 到 150 GB</td> <td>前 50 个 GB 为 12.6 DU，<br>每个额外的 GB 为 0.1 DU</td> </tr> </tbody> </table></li><ul>