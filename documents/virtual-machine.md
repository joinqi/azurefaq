# 虚拟机创建及管理

#### 附加磁盘的时候,虚机是否会重启?
>虚拟机不会重启.在auzre管理平台中附加完成后,用户需要进入虚拟机中,做磁盘挂载.否则附加的磁盘还是不可用的

#### 如何对虚拟机的进行硬件配置升级
>进入虚拟机的配置画面,选择对应的升级模板,保存后会自动升级.
**配置保存后会虚拟机会重启,重启后公网IP有可能发生变动***

#### 删除虚拟机,对应的vhd会被删除吗?
>不会删除.还会存在于虚拟机的*磁盘*标签列表,在存储的vhds列表容器中也可见.如果需要彻底删除,可以在*磁盘*标签列表中选择"删除关联的VHD";如果是需要保留数据盘,可以选择"保留关联的VHD"

#### 如何捕获一个映像?会产生什么附带影响?捕获的映像有什么用处?
>虚拟机关机状态可以捕获映像,同时会将虚拟机删除.捕获的映像可以用做创建虚拟机的模板,比如已经安装好jdk,apache,下次创建虚拟机就不用做这些重复工作。
使用方法新建->计算->虚拟机->从库中,在弹出的界面选择"我的映像",即可看到
![](/images/vm-1.01.jpg)

#### 虚拟机配置端点有限制吗?
>端点最大数量是150个,私有端口不建议修改.如果确实需要修改,虚拟机的防火墙要做对应的改动

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

#### 虚拟机的公网虚拟 IP 是固定的吗?
>虚拟机的公网虚拟 IP 不是固定的,虚拟机重启或者重建后,Windows Azure都会重新分配公网虚拟 IP .应用系统应该用 DNS地址 代替 IP 配置 

[返回首页](</index.md>)



