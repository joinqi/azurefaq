# 虚拟机

#### 附加磁盘的时候,虚机是否会重启?
>虚拟机不会重启.在auzre管理平台中附加完成后,用户需要进入虚拟机中,做磁盘挂载.否则附加的磁盘还是不可用的

#### 如何对虚拟机的进行硬件配置升级
>进入虚拟机的配置画面,选择对应的升级模板,保存后会自动升级.
**配置保存后会虚拟机会重启,重启后公网IP有可能发生变动**

#### 删除虚拟机,对应的vhd会被删除吗?
>不会删除.还会存在于虚拟机的*磁盘*标签列表,在存储的vhds列表容器中也可见.如果需要彻底删除,可以在*磁盘*标签列表中选择"删除关联的VHD";如果是需要保留数据盘,可以选择"保留关联的VHD"

#### 如何捕获一个映像?会产生什么附带影响?捕获的映像有什么用处?
>虚拟机关机状态可以捕获映像,同时会将虚拟机删除.捕获的映像可以用做创建虚拟机的模板,比如已经安装好jdk,apache,下次创建虚拟机就不用做这些重复工作。
使用方法新建->计算->虚拟机->从库中,在弹出的界面选择"我的映像",即可看到
![](/images/vm-1.01.jpg)

#### 虚拟机配置端点有限制吗?
>端点记录最多可以建 *150* 个.没有特殊服务的私有端口建议不要修改.如果确实需要修改,虚拟机的防火墙或者系统要做对应的改动。
 *150* 个端点是总的记录数。如果仅仅只需要开放2014端口，但需要开通TCP和UDP协议，需要增加两个端点记录。以后只能增加 *150-2=148* 笔端点记录了

#### 多台虚拟机如何配置负载均衡?
>虚拟机的负载均衡是通过端口检测完成。具体操作步骤见[对虚拟机进行负载平衡](http://windowsazure.cn/zh-cn/manage/linux/common-tasks/how-to-load-balance-virtual-machines/)

#### 虚拟机挂载磁盘有什么限制?
>虚拟机按照不同规格,挂载的磁盘数量有限制,具体如下
<table>
 <tbody><tr>
 <th>大小</th><th>CPU 内核数</th><th>内存</th><th>最大数据磁盘数（每个磁盘 1 TB）</th></tr>
 <tr><td><strong>ExtraSmall</strong></td><td>共享</td><td>768 MB</td><td>1</td></tr>
 <tr><td><strong>Small</strong></td><td>1</td><td>1.75 GB</td><td>2</td></tr>
 <tr><td><strong>Medium</strong></td><td>2</td><td>3.5 GB</td><td>4</td></tr>
 <tr><td><strong>Large</strong></td><td>4</td><td>7 GB</td><td>8</td></tr>
 <tr><td><strong>ExtraLarge</strong></td><td>8</td><td>14 GB</td><td>16</td></tr>
 <tr><td><strong>A5</strong></td><td>2</td><td>14 GB</td><td>4</td></tr>
 <tr><td><strong>A6</strong></td><td>4</td><td>28 GB</td><td>8</td></tr>
 <tr><td><strong>A7</strong></td><td>8</td><td>56 GB</td><td>16</td></tr>
</tbody></table>
详细规格[链接](http://msdn.microsoft.com/zh-cn/library/windowsazure/dn197896.aspx)  

#### 虚拟机临时存储是否收费?挂载的磁盘如何收费?
>Azure上所有的存储都是按照使用量收费,比如你挂载了 500 GB 的磁盘,只使用了 10 MB,只收 10 MB 的费用.  

#### 虚拟机的公网虚拟IP是固定的吗?内部IP地址也是固定的吗？
>虚拟机的公网虚拟IP是固定的。公网虚拟IP是和云服务DNS关联，而虚拟机是和云服务DNS关联，所以虚拟机，关闭，启动和重启,或者在此云服务下重建，只要对应的云服务没有关闭，且在该云服务下总有一台虚拟机开启着，公网虚拟 IP 就不会变.  
如果设定了虚拟网络，虚拟机的内部网络IP重启的时候不会变，关机后再启动可能会变

#### 虚拟机运行过程中产生的网络流量和磁盘IO操作会另外计费吗?
>Windows Azure Mooncake 版本的网络流量和磁盘IO操作理论上是*收费*的.但是对 ENROLLMENT 有一个免费的用量数,超过这个用量数才会收费,并且收费标准和 International 也有区别,具体的价格需要参考 Windows Azure Mooncake 的公开报价.

#### 是否可以在一个云服务下创建多台虚拟机？同一云服务下的多台虚拟机如何连接？
>Azure支持在同一个云服务下创建多台虚拟机。一个云服务相当于一个公网的IP地址，所以在Azure中云服务算是一种比较稀缺的资源。在没有特别端口要求的情况下应尽可能在一个云服务下创建多个虚拟机。在同一云服务下的不同虚拟机可以用不同的Remote端口号进行区分，也可以直接通过下载RDF文件来直接连接。

#### 在同一个云服务下创建多台虚拟机都有哪些注意事项？
>在同一个云服务下创建多台虚拟机后，由于公用虚拟IP地址只能是云服务来提供，所以在为不同虚拟机开放公有端口是可能会出现冲突。另外如果多台虚拟机同时开放了相同的公有端口，Azure可以对这些虚拟机创建负载均衡。

#### 当在网络端口被限制的网络中该如何进行创建规划虚拟机？
>以Windows系列操作系统为例。首先确定Windows远程桌面端口（3389）可以使用。如果3389端口可以使用，那么可以将虚拟机的远程连接端点中的公有端口也设置为3389来达到访问虚拟机的目的。当同时有多台虚拟机共用一个云服务时，由于端口占用问题只能有一个台虚拟机开放3389端口，其他虚拟机应采用跳板（Second hop）方式来登陆。如果有必要，可以将跳板机上的Terminal Service打开，来满足多人同时登陆的需求。如果3389端口也被禁用了，可以采用创建一个Point to Site的VPN来将本地机器接入虚拟子网来实现登陆的效果。

#### 内部IP地址与公用虚拟IP（VIP）地址有什么区别？
>内部IP地址是Azure内部的IP地址，相当于一个局域网中的IP地址，如果在几台虚拟机在同一个虚拟网络中，可以通过内部IP地址进行互访。公用虚拟IP（VIP）地址，是一个虚拟的公网IP，相当于一个对外的地址，连接在公网的机器可以通过这个地址来访问到Azure上的机器。

#### 同一个虚拟网络里在不配置公共端口的情况虚机是否可以互访？
>可以互相访问，通过内部IP地址可以访问在同一个虚拟子网下的各个虚机。

#### 如何突破Azure虚拟机单块磁盘容量上限？
>可以采用Striping Volume to Data Disks的方式，具体步骤参考这篇[文档](https://www.simple-talk.com/cloud/infrastructure-as-a-service/windows-azure-virtual-machine-a-look-at-windows-azure-iaas-offerings-(part-2)/)

#### 如何将Azure虚拟机配置为文件服务器并配置共享文件夹？
>请参考以下文档：[How to Configure a Windows Azure Virtual Machine File Server](http://blogs.msdn.com/b/philpenn/archive/2012/08/30/how-to-configure-a-windows-azure-virtual-machine-file-server-and-use-it-from-within-windows-hpc-server-compute-jobs.aspx)

#### 如何将Azure虚拟机配置为FTP服务器？
>请参考以下文档：[Hosting FTP on IIS 7.5 in a Windows Azure VM](http://itq.nl/walkthrough-hosting-ftp-on-iis-7-5-a-windows-azure-vm-2/)

#### SQL Server License问题，在Azure上创建虚拟机后，如果自己安装SQL Server，License必须使用可以动的账号，如果使用普通的License出现问题的话，出现什么样的状况，微软不提供技术支持？
>并非所有微软产品的license都可以在VM进行部署的，有的license只可以在物理服务器上进行部署，具体情况请查阅产品license文档，或者咨询相应的产品团队。尽量使用SQL Azure代替SQL Server，这样可以充分享受到Windows Azure PaaS所带来的好处，包括成本、扩展性，伸缩性。

#### 关于99.95%运行保障，必须做到所有服务器均设置为双机同步备份，才能支持吗？如果只做了单机，发生故障。恢复时间是否有说明？
>理论上只有在可用集里面的VM才可以达到99.95%的SLA，这也是微软官方推荐的做法。其实，对于Windows Azure而言，如果能忍受每1~2个月一次，每次1~2分钟的重启，那么，用户可以结合成本因素自行决定是否部署双机。对于使用VM的用户，需要特别注意一点，一定不要将重要数据保存在VM自带的数据盘上，例如Windows系统中的D盘。VM自带的数据盘会因VM重建或调整而丢失。正确的做法是在Storage中创建一个VHD，然后将VHD挂载到VM中作为磁盘使用，这样，即便VM挂掉了，数据也可以确保万无一失。

#### Windows Service多用户登陆问题
>在有网络端口限制的情况下，有可能需要配置Windows Server的多用户登陆即Remote Desktop Service，具体步骤请参见此[文档](http://blog.csdn.net/lanwilliam/article/details/6338493)

#### 远程登录到虚拟机操作系统中关闭了虚拟机，Windows Azure还会收费吗？
>会，虽然虚拟机已经关闭了，但还是占用着 Windows Azure的内存，CPU资源。所以正确的做法应该是通过 Windows Azure 管理平台或 API 来关闭虚拟机。

[返回首页](</index.md>)



