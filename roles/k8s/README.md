Role  k8s
=========

使用Kubernetes官方工具kubeadm快速部署k8s集群。

目前实现功能:

- 一键快速拉起一个单master多node的原生k8s集群.
- 支持部署最新1.16.2和稳定版1.15.5
- 支持可选几种网络插件，详情参考default/main.yaml
- 安装配置了自带的dashboard
  
暂未实现, todo:
- 支持高可用集群部署
- 支持直接部署ingress
- 支持

Requirements
------------

- OS: RHEL/CentOS >= 7.5
- Docker: docker-ce >= 18.06.2-ce

Role Variables
--------------

默认环境变量保存在`default/main.yaml`中,要想知道支持哪些变量可以查看此文件.

当前支持的配置变量:

**注意** : 目前k8s核心组件到版本跟etcd和coredns是配套的，详情参见`default/main.yaml`里的变量.

- master_ip_address
- k8s_version
- coredns_tag
- etcd_tag
  


Dependencies
------------

- 如果kube-proxy网络模式使用IPVS,在所有节点上必须安装ipvsadm,以及加载ipvs的内核模块.
- 要求部署有本地仓库，因为默认使用k8s.gcr.io上的镜像，国内是无法直接下载的，只能提前准备好私有仓库镜像.

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    - hosts: servers
      roles:
         - { role: k8s, k8s_version: v1.16.2 }

License
-------

BSD

Author Information
------------------

An optional section for the role authors to include contact information, or a website (HTML is not allowed).
