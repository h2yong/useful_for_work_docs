# python

- https://www.learnbyexample.org/python-introduction/

## python web 框架

- [reflex](https://reflex.dev/)
- [Django](https://docs.djangoproject.com/zh-hans/5.2/)
- [flask](https://flask.org.cn/en/stable/)
- [streamlit](https://streamlit.io/)
- [Gradio](https://gradio.org.cn/guides/quickstart)
  - [Gradio入门到进阶全网最详细教程[一]：快速搭建AI算法可视化部署演示(侧重项目搭建和案例分享)](https://zhuanlan.zhihu.com/p/624712372)
- [dash](https://plotly.com/dash/)
- [FastAPI](https://fastapi.org.cn/tutorial/first-steps/)

## python 虚拟环境

- [Python 包与虚拟环境工具全景对比：从 virtualenv 到 uv 的演进](https://jishuzhan.net/article/1954852619268173826)
- [Python 包管理及环境管理工具对比](https://www.cnblogs.com/dokibook/p/19049003)
- [Python 專案管理工具全面比較 - uv, Poetry, Pixi, Hatch, PDM, Conda, Mamba, Pipenv, venv, virtualenv](https://dev.to/zhenshuo2021/best-python-project-manager-288p)
  > https://zsl0621.cc/python/best-python-project-manager
- [【基础】Python 包及环境管理工具大盘点：pip、pipx、poetry、conda、pipenv、Pixi、uv、venv、virtualenv、pyenv 、Mamba、Hatch、PDM 等](https://blog.csdn.net/2501_90561511/article/details/147732638)

## cuda windows 安装

- [CUDA 与 CUDNN 在 Windows 下的安装与配置](https://blog.csdn.net/YYDS_WV/article/details/137825313)
- [windows 上使用 anconda 安装 tensorrt 环境](https://zhuanlan.zhihu.com/p/680098295)

### CUDA lazy loading is not enabled

**背景**:  
在 TensorRT 运行测试用例的时候出现以下`warning：CUDA lazy loading is not enabled. Enabling it can significantly reduce device memory usage and speed up TensorRT initialization. See "Lazy Loading" section of CUDA documentation https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html#lazy-loading`

**解决方案**:  
启用懒加载需设置环境变量 CUDA_MODULE_LOADING=LAZY，适用于 CUDA 版本 11.7 及以上。

**参考文档**:

- [CUDA lazy loading is not enabled. Enabling it can significantly reduce device memory usage and speed](https://blog.csdn.net/s1_0_2_4/article/details/135026761)

## python 技术文章未分类

- [五彩斑斓的 Black —— Python 代码格式化工具](https://muzing.top/posts/a29e4743/)
- [pytest 多进程/多线程执行测试用例](https://www.cnblogs.com/micheryu/p/16441492.html)
- [pytest 中使用 mock](https://note.qidong.name/2018/02/pytest-mock/)
- [ModuleNotFoundError: No module named 'fcntl'](https://blog.51cto.com/mouday/5805526)
- [如何在 Python 中计算平均数](https://juejin.cn/post/7114916117956526088)
- [Python 日志库 logging 总结](https://blog.51cto.com/u_15293910/3061800)
- [常用正则表达式速查手册，Python 文本处理必备](https://juejin.cn/post/7033584212821147679)
- [正则表达式中(?\:pattern)、(?=pattern)、(?!pattern)、(?<=pattern)和(?\<!pattern) ](https://www.cnblogs.com/dogecheng/p/11466687.html)
- [Python | Split dictionary keys and values into separate lists](https://www.geeksforgeeks.org/python-split-dictionary-keys-and-values-into-separate-lists/?ref=ml_lbp)
- [Python 使用 cn2an 实现中文数字与阿拉伯数字的相互转换](https://www.jb51.net/article/206606.htm)
- [Python-100-Days](https://github.com/jackfrued/Python-100-Days/blob/master/Day91-100/96.%E8%BD%AF%E4%BB%B6%E6%B5%8B%E8%AF%95%E5%92%8C%E8%87%AA%E5%8A%A8%E5%8C%96%E6%B5%8B%E8%AF%95.md)
- [Python 中强大的通用 ORM 框架：SQLAlchemy](https://zhuanlan.zhihu.com/p/444930067)
- [Pytest 权威教程(官方教程翻译)](https://www.cnblogs.com/superhin/p/11677240.html)
- [chatgpt-on-wechat](https://github.com/zhayujie/chatgpt-on-wechat)
- [JioNLP](https://github.com/dongrixinyu/JioNLP)
- [awesome-chinese-nlp](https://github.com/crownpku/Awesome-Chinese-NLP)
- [CLUE benchmark](https://github.com/CLUEbenchmark/CLUE)
- [NLP 民工的乐园: 几乎最全的中文 NLP 资源库](https://github.com/fighting41love/funNLP)
- [中文近义词：聊天机器人，智能问答工具包 Synonyms](https://github.com/chatopera/Synonyms)
- [LangChain 中文入门教程](https://github.com/liaokongVFX/LangChain-Chinese-Getting-Started-Guide)
- [serpapi](https://serpapi.com/manage-api-key)
  > github 帐号登录
- [pydantic 学习与使用-2.基本模型(BaseModel)使用](https://www.cnblogs.com/yoyoketang/p/15908037.html)
- [LangChain 中文网](https://www.langchain.com.cn/)
- [LangChain-Chatchat](https://github.com/chatchat-space/Langchain-Chatchat)
- [MedicalGPT](https://github.com/liuhuanyong/MedicalGPT)
- [AI 算法测评(五)--算法测试实践](https://www.cnblogs.com/pojason/p/14629055.html)
- [Gunicorn的使用手册看这篇就够了](https://cloud.tencent.com/developer/article/1902723)
- [vs code、pycharm配置ruff](https://blog.csdn.net/randy521520/article/details/146119542)

## 依赖项管理

- [poetry](https://python-poetry.cn/docs/)
- [uv](https://uv.doczh.com/)
  - 设置国内源: 新增环境变量`UV_DEFAULT_INDEX=https://mirrors.cloud.tencent.com/pypi/simple`
  - [docker 使用 uv 安装依赖](https://blog.csdn.net/QAZJOU/article/details/146515583)
  - `ghcr.io/astral-sh/uv`国内镜像: <https://docker.aityp.com/image/ghcr.io/astral-sh/uv:latest>
  - [astral-sh/uv 教程](https://opendeep.wiki/astral-sh/uv/faq)