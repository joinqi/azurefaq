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
<th>大小
</th>
<th>
CPU 内核数
</th>
<th>
内存
</th>
<th>
最大数据磁盘数<br>（每个磁盘 1 TB）
</th>
 
</tr>
<tr>
<td>
  <p>
<strong>ExtraSmall</strong>
  </p>
</td>
<td>
  <p>共享</p>
</td>
<td>
  <p>768 MB</p>
</td> 
<td>
  <p>1</p>
</td>
</tr>
<tr>
<td>
  <p>
<strong>Small</strong>
  </p>
</td>
<td>
  <p>1</p>
</td>
<td>
  <p>1.75 GB</p>
</td>
<td>
  <p>2</p>
</td>
</tr>
<tr>
<td>
  <p>
<strong>Medium</strong>
  </p>
</td>
<td>
  <p>2</p>
</td>
<td>
  <p>3.5 GB</p>
</td>
<td>
  <p>4</p>
</td>
</tr>
<tr>
<td>
  <p>
<strong>Large</strong>
  </p>
</td>
<td>
  <p>4</p>
</td>
<td>
  <p>7 GB</p>
</td>
<td>
  <p>8</p>
</td>
</tr>
<tr>
<td>
  <p>
<strong>ExtraLarge</strong>
  </p>
</td>
<td>
  <p>8</p>
</td>
<td>
  <p>14 GB</p>
</td>
<td>
  <p>16</p>
</td>
</tr>
<tr>
<td>
  <p>
<strong>A5</strong>
  </p>
</td>
<td>
  <p>2</p>
</td>
<td>
  <p>14 GB</p>
</td>
<td>
  <p>4</p>
</td>
</tr>
<tr>
<td>
  <p>
<strong>A6</strong>
  </p>
</td>
<td>
  <p>4</p>
</td>
<td>
  <p>28 GB</p>
</td>
<td>
  <p>8</p>
</td>
</tr>
<tr>
<td>
  <p>
<strong>A7</strong>
  </p>
</td>
<td>
  <p>8</p>
</td>
<td>
  <p>56 GB</p>
</td>
<td>
  <p>16</p>
</td>
</tr>
  </tbody></table>
#### 虚拟机临时存储是否收费?挂载的磁盘如何收费?
>Azure上所有的存储都是按照使用量收费,比如你挂载了 500 GB 的磁盘,只使用了 10 MB,只收 10 MB 的费用.



