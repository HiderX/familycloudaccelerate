# 天翼家庭云APP 破解提速脚本

## 说明
脚本思路:[Ruter's Journal](http://blog.ruterfu.com/2019/02/09/faster-upload-using-tianyicloud/)
破解思路以及Java程序，编写的Python脚本  
依赖环境: Python2 | Python3 , requests
## 依赖环境安装
`Ps:` 已经尝试用 python 原生 urllib 库来发送http包,但是服务端恶意返回 400 状态码(原生库无法识别), 原生库抛异常无法读取数据.  
所以请使用pip安装requests
```shell
pip install requests
```
## 使用方法

1. 采用 [手机端抓包方法](https://github.com/aiyijing/familycloudaccelerate/wiki/%E5%AE%B6%E5%BA%AD%E4%BA%91%E6%89%8B%E6%9C%BA%E7%AB%AF%E6%8A%93%E5%8C%85%E6%96%B9%E6%B3%95)  (建议使用手机端抓包方法) 或参照[Ruter's Journal](http://blog.ruterfu.com/2019/02/09/faster-upload-using-tianyicloud/) 思路进行APP抓包，获取`session_key`,`session_secret` 
2. 将参数填入config.json 并且酌情修改其他参数
```python
{
    "session_key":"session_key",    # 必填 session_key
    "session_secret":"session_secret",# 必填 session_secret
    "setting":{
        "method":"POST",        # 可选:POST|GET
        "rate":600              # 心跳包频率 单位秒 建议修改为600
    },
    "send_data":{
          "prodCode": "76",     # 默认
          "version": "2.0.10",  # app 版本
          "channelId": "web"    # 默认参数
    },
    "extra_header":{
        "User-Agent": "Apache-HttpClient/UNAVAILABLE (java 1.4)"    #附加HTTP Header
    }
}
```  
3. 请选择相应版本的python脚本,运行程序  
python FamilySpeedUp.py


## TODO
1. 能正常提速,但是无法获取提速结果,需要修改相关接口
2. Python版本程序不便于移植嵌入式平台如:openwrt,正在编写GO语言版本以便于移植

欢迎大家提 ISSUE 本人定当竭力相助