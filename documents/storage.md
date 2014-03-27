# 存储

#### 使用Blob的限制
>Blob分为两种，区块Blob和页Blob    
><ul>
><li>区块Blob</li>
>这类的存储以4MB为一个区块单位，单一文件最大可以存储200GB，且区块不会连续存储，可能会打散到不同的存储服务器中存放，当应用程序要求时，会依照文件的Key以及区块由存储区提取数据。。在上载块Blob时，小于64MB的文件可以被一次性写入。更大的文件是分Block上载的，每个Block最大可达4MB。一个Blob中最多可以包含50000个这样的Block。在所有Block上载后，需要上载一个Block列表以供存储服务把这些Block装配程一个完整的Blob。在上载的过程中可以并发上载多个Block，且不需要按顺序上载。所有上载的块都处于一种“未提交”的状态，直到进行提交操作。Block上载的时候，可以利用CloudBlockBlob类上的PubBlock方法来提交Block，然后用PutBlockList方法提交Block列表。
><li>标签页Blob</li>
>页Blob最大可以达到1TB。会在存储区中划分一个连续的区域供应用程序存放数据,一个页Blob有多个512B的页构成，页Blob适用于随机读写操作。在创建一个页Blob时需要指定Blob能占用的最大空间。在读写时要按着512B的边界来进行。与块Blob不同，使用页Blob的所有的更新都是立即提交的，而不需要一个单独的提交操作。
></ul>

#### 使用表的限制
>Azure中表存储服务中表（Table）是一个实体的集合。与传统数据库不同，存储服务表没有固定的结构，也就是说可以在同一张表内存入含有不同字段的记录。实体是一个属性的集合，类似于关系数据库中的一行记录。一个实体最大可达1MB。属性是一个键-值对。每个实体可以最多有252个属性。每个实体有个3个系统保留属性，分别是分区键、行健和时间戳。位于同一分区的实体可以作为一个原子操作来插入或查询。每个分区内的行健必须是唯一的。

#### Windows Azure主机缓存
>Windows Azure虚拟机中，操作系统磁盘和数据盘都有一个主机缓存选项，用来提升某些情况下应用的性能。默认情况下，对于数据磁盘的读写操作主机缓存都关闭的，而对于操作系统盘的读写操作的主机缓存都是开启的。
>主机缓存是一个磁盘缓存，其中读缓存是写通过形式的磁盘缓存，读/写缓存是回写式的磁盘缓存。

#### Azure存储冗余机制
>Windows Azure包含三种存储冗余机制，包括本地冗余、地理冗余和处于预览阶段的读取访问地域冗余。默认每个Storage Account的冗余机制是地理冗余。详细内容可以参见下面两篇文章。
>[Windows Azure Storage Redundancy Options and Read Access Geo Redundant Storage](http://blogs.msdn.com/b/windowsazurestorage/archive/2013/12/04/introducing-read-access-geo-replicated-storage-ra-grs-for-windows-azure-storage.aspx)
>[Data Series: Introducing Locally Redundant Storage for Windows Azure Storage](http://blogs.msdn.com/b/windowsazure/archive/2012/06/08/introducing-locally-redundant-storage-for-windows-azure-storage.aspx)

#### Azure存储控制
>Windows Azure可以通过共享访问签名来将存储账户中的文件共享给其他用户而不用暴露出你的存储账户访问密钥。详细信息参见下面两篇文章。
>[Shared Access Signatures, Part 1: Understanding the SAS Model](http://www.windowsazure.com/en-us/documentation/articles/storage-dotnet-shared-access-signature-part-1/?fb=zh-cn)
>[Shared Access Signatures, Part 2: Create and Use a SAS with the Blob Service](http://www.windowsazure.com/en-us/documentation/articles/storage-dotnet-shared-access-signature-part-2/?fb=zh-cn)

[返回首页](</index.md>)