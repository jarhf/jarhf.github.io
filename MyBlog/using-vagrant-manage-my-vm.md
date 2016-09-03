#prerequisites
1. install [VirtualBox](https://www.virtualbox.org/wiki/Downloads). Remember download and install VirtualBox Extension Pack
2. install [Vagrant](https://www.vagrantup.com/downloads.html)
3. After install VirtualBox and Vagrant, run cmd : 
4. `vagrant init jhcook/osx-elcapitan-10.11; vagrant up --provider virtualbox` to install OS X in vagrant.  
> You can search Vagrant boxes on https://atlas.hashicorp.com/boxes/search.


**change default boxes download save folder**

 ```
 //need windows Command Prompt (Admin)
 setx /M VAGRANT_HOME D:\ProgramData\.vagrant.d
 ```

## Useful cmd

* 改变默认的box存储路径
```
//设置环境变量  /m 表示设置 machine
setx VAGRANT_HOME D:\ProgramData\Vagrant\.vagrant.d /m  (需要admin)  
```
* 安装box  `vagrant box add Win7_x86 http://aka.ms/vagrant-win7-ie11 或者本地xx.box `
* 初始化：`vagrant init Win7_x86`     (建议先mkdir一个Win7文件夹，再初始化到该目录下)  
* 查看全局:  `vagrant global-status  `
* 查看所有boxes：`vagrant box list  `
* 启动： `vagrant up `, 需要先cd到指定 init目录下。
* 关闭： `vagrant halt`
* 重置： `vagrant destroy <Win7_x86>`
