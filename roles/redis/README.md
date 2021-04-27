```
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
```

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
