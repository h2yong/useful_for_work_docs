# Conda使用指南
> conda是一个开源包管理系统和环境管理系统，用于安装多个版本的软件包及其依赖关系，并在它们之间轻松切换。

## Conda安装
Anaconda是一个开源的Python发行版本，包含了conda、python等180多个科学包及其依赖项。下载地址如下：  
- 官方站：https://www.anaconda.com/products/individual-d
- 国内镜像站：https://mirrors.tuna.tsinghua.edu.cn/anaconda/archive/

Miniconda是最小的conda安装环境。下载地址如下：  
- 官方站：https://conda.io/miniconda.html
- 国内镜像站：https://mirrors.tuna.tsinghua.edu.cn/anaconda/miniconda/

## Conda的环境管理
### 显示所有的环境
```bash
$ conda env list
$ conda info --envs
```

### 创建一个新的虚拟环境
```bash
$ conda create -n $env_name python=3.6
# example
$ conda create --name py39 python=3.9
```

### 激活虚拟环境
```bash
$ conda activate $env_name
# example
$ conda activate py39

$ activate $env_name # for Windows
# example
$ activate py39 # for Windows

$ source activate $env_name # for linux
# example
$ source activate py39 # for linux
```

### 退出虚拟环境
```bash
$ deactivate $env_name # for Windows
# example
$ deactivate py39 # for Windows

$ source deactivate $env_name # for linux
# example
$ source deactivate py39 # for linux
```

### 删除环境
```bash
$ conda remove --name $env_name --all # 删除一个已有的环境
# example
$ conda remove --name py39 --all # 删除一个已有的环境

$ conda remove --name $env_name $package_name      # 删除环境中的某个package
# example
$ conda remove --name py39 requests      # 删除环境中的某个package
```

## Conda的包管理
### 安装包
```bash
# 为当前环境安装package
$ conda install $package_name
# example
$ conda install requests

# 安装package到指定环境
$ conda install -n py39 $package_name
# example
$ conda install -n py39 requests
```

### 更新包
```bash
# 为当前环境更新package
$ conda update $package_name
# example
$ conda update requests

# 更新package到指定环境
$ conda update -n py39 $package_name
# example
$ conda update -n py39 requests
```

### 删除包
```bash
# 从当前环境删除package
$ conda remove $package_name
# example
$ conda remove requests

# 从指定环境删除package
$ conda remove -n py39 $package_name
# example
$ conda remove -n py39 requests
```

## 更新conda
```bash
# 更新conda，保持conda最新
$ conda update conda
```

## 更新python
```bash
# 假设当前环境是python3.9, conda会将python升级为3.9.x系列的当前最新版本
$ conda update python
```