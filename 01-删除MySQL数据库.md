系统：`Windows10`

删除之前，请先保存重要的数据库文件：

自定义路径的就应该自己知道。

这是默认路径：

`C:\ProgramData\MySQL\MySQL Server 5.5\Data\`

默认的文件，属于隐藏文件，打开时，需要打开：查看，选择隐藏的项目

![1](https://github.com/1004032560/MySQL/blob/master/image/01-01.png?raw=true)



![2](https://github.com/1004032560/MySQL/blob/master/image/01-02.png?raw=true)





1、停止`MySQL`服务

此电脑->管理->服务与应用程序->服务->找到`MySQL`->停止

 注意：`MySQL80`是安装解压包时自动安装的，`MySQL`是你自己又初始化后安装的，都停止掉

![3](https://github.com/1004032560/MySQL/blob/master/image/01-03.png?raw=true)

 ![4](https://github.com/1004032560/MySQL/blob/master/image/01-04.png?raw=true)



2、卸载`MySQL Server`

设置->控制面板->程序和功能->找到和`MySQL`相关的都卸载掉

![5](https://github.com/1004032560/MySQL/blob/master/image/01-05.png?raw=true)



![6](https://github.com/1004032560/MySQL/blob/master/image/01-06.png?raw=true)



![7](https://github.com/1004032560/MySQL/blob/master/image/01-07.png?raw=true)



3、删除`MySQL`文件夹

在对应的`MySQL`安装的位置，删除整个文件夹；同时，删除掉`C:\ProgramData\MySQL\`目录下的`MySQL`文件夹，这是个隐藏文件，打开方式已经找过了。

有些地方说的是删除`C:\Documents and Settings\All Users\Application Data\MySQL` 这个隐藏目录下的`MySQL`，但是我在我自己的`Win10`上找了好久没找到，原来是被`ProgramData`目录给直接替换了。

所以，有哪个就把哪个删掉就行。



2、删除注册表

方式一：

`win`键`+R`打开之后输入`regedit`，打开注册表。

`Ctrl+F`查找，输入关键字`MySQL`进行删除。

方式二：（建议方式二，在这几个目录下查找删除）

* `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\Eventlog\Application\MySQL`文件夹。
* `HKEY_LOCAL_MACHINE\SYSTEM\ControlSet002\Services\Eventlog\Application\MySQL`文件夹。
* `HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Eventlog\Application\MySQL`的文件夹。

如果没有相应的文件夹，就不用删除了。

![8](https://github.com/1004032560/MySQL/blob/master/image/01-08.png?raw=true)



![9](https://github.com/1004032560/MySQL/blob/master/image/01-09.png?raw=true)



 以上步骤完成之后即可重装`MySQL`。