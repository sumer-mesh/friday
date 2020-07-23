Description
├── defaults
│   └── main.yml
├── files
├── handlers
│   └── main.yml
├── README.md
└── tasks
    ├── main.yml
    ├── offline-install.yml
    └── online-install.yml

Instruction

This package provides online and offline installation of two ways

Choice of installation methods

1. If you do not specify the default is to install online
2. Online local storage unit that is installed in 10.116.18.67
3. If you need to specify when running offline installation requires 2 parameters
   - 1) Need to specify the remote location of the installation package
   - 2) deploy_mode the need to specify the installation mode for offline

  for example1: 
   
  ```
    ansible-playbook -i hosts  deploy.yml  -e "deploy_mode=offline" -e "packagedir=/Users/devops/Desktop/workspace/RPMS"

  ```

   `packagedir=/users/devops/desktop/workspace/rpms` specified here is the native storage of the package directory.
   Offline installation mode must be specified to `deploy_mode=offline`, the default is to use the online installation.



Envrionmental Dependency

ansible

Version

v1.0 2019.11.21



说明
├── defaults
│   └── main.yml
├── files
├── handlers
│   └── main.yml
├── README.md
└── tasks
    ├── main.yml
    ├── offline-install.yml
    └── online-install.yml

====
**用途**
 本安装包提供离线与在线安装两种方式

====
 安装方式的选择

1. 如果不指定默认就是在线安装
2. 在线安装的本地仓库地址在10.116.18.67
3. 如果采用离线安装需要运行的时候需要指定2个参数
  - 1）需要指定远程安装包所在位置
  - 2）需要指定安装模式deploy_mode为offline

   for example1: 
   
  ```
    ansible-playbook -i hosts  deploy.yml  -e "deploy_mode=offline" -e "packagedir=/Users/devops/Desktop/workspace/RPMS"
  ```
   这里指定的`packagedir=/Users/devops/Desktop/workspace/RPMS`是本机存放的文件包目录.
   离线安装模式必须要指定`deploy_mode=offline`，默认是使用在线安装方式.


  
环境依赖

需要安装ansible

版本发布

v1.0 2019.11.21