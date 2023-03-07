# lenovo-sign-ql
联想智选签到
适配青龙面板

**使用须知：**  
**1. 使用的Python版本必须大于等于Python3.8**  
**2. 定时执行的任务必须放到中午十二点以后（推荐中午十二点），本人在早上八九点测试有问题**

## 本地使用

1. 克隆本仓库
```bash
git clone https://github.com/marigold233/lenovo-sign.git
```
2. 安装依赖
```bash
pip3 install -r requirements.txt
```
3. 在`config.toml`填入你的账号和选择推送通知的类型，也可以不选择推送，不填即可
4. 测试运行脚本
```bash
python3 lenovo_sign.py
```
5. 加入crontab计划任务

```bash
# 查看python3解释器绝对路径，crontab里面要写解释器绝对路径
which python3
/usr/local/bin/python3
# 每天中午12点运行
0 12 * * * /usr/local/bin/python3 /root/lenovo_sign.py &> lenovo_sign.log
```
## ~~腾讯云函数使用~~

1. 将云函数目录里面的`index.py`代码复制粘贴到腾讯云函数里面的`index.py`
2. 创建文件`config.toml`，将`config.toml`里面的配置也复制进去
3. 安装`requirements.txt`里面的依赖
```bash
cd src
pip3 install requests toml --upgrade -t .
```
4.   在`config.toml`按照配置你的账号和选择推送通知的类型，也可以不选择推送，不填即可
5. 完成！部署测试

## 阿里云函数使用

1. 将云函数目录里面的`index.py`代码复制粘贴到阿里云函数里面的`index.py`
2. 创建文件`config.toml`，将`config.toml`里面的配置也复制进去
3. 安装`requirements.txt`里面的依赖
```bash
pip3 install requests toml --upgrade -t .
```
4.   在`config.toml`按照配置你的账号和选择推送通知的类型，也可以不选择推送，不填即可
5. 完成！部署测试

## 青龙面板使用

1. 安装脚本依赖`requests toml`
2. 把文件`lenovo_sign.py`,`config.toml`上传到青龙面板
3. 在`config.toml`里面填写账号和推送
4. 完成！进行测试

## 支持推送消息类型

- server酱
- 企业微信应用
- 钉钉群机器人

## 更新
- 2022.10.26
	1. 优化云函数代码
	2. 获取乐豆和延保信息失败导致脚本出现异常，对异常进行处理
- 2022.10.19
	1. 多账号签到，账号密码错过略过，不影响下面签到的账号
- 2022.10.18
	1. 优化代码
- 2022.10.13  
	1. 钉钉推送
- 2022.08.16
	1. 添加签到消息推送
- 2022.08.07
	1. 修复签到不给延保的问题  
- 2022.06.20  
	1. 优化本地版本  
	2. 支持云函数  
- 2022.06.17  
	1. 支持类手机签到，送延保券。以前的版本不给。
