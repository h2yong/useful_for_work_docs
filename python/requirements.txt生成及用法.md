

# requirements.txt生成及用法
>  requirement.txt一般放在项目根目录下，用于记录项目所有依赖包和它的确切版本号。

# 单虚拟环境生成requirements.txt
```bash
pip freeze > requirements.txt
```

此方式会将环境中的依赖包全都加入，如果使用的全局环境，则下载的所有包都会在里面，不管是不是当前项目依赖的。故此种方式不适合python项目。

# 使用pipreqs生成requirements.txt
使用pipreqs生成requirements.txt只生成项目依赖的包，不会将全局环境所有包都生成。

1. 安装pipreqs
```bash
pip install pipreqs
```

2. cd到项目根目录，执行以下命令生成requirements.txt
```bash
pipreqs ./ --encoding=utf8 --force
```

## 利用requirements.txt安装依赖包
### 在线安装依赖包

```bash
pip install -r requirements.txt
```

### 离线安装依赖包
1. 打包已安装的包
```bash
pip install --download {packagesdir} -r requirements.txt
```

2. 安装离线包
```bash
pip install --no-index --find-links={packagesdir} -r requirements.txt
```

> {packagesdir}为python离线包路径，如：d:\python39\packages