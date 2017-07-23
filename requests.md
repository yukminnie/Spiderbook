# Requests 笔记


---
```
1.实例引入
import requests

response = requests.get('http://www.baidu.com/')
print(type(response))    
print(response.text)
print(response.status_code)
print(response.cookies)

2.各种请求方式

import requests

rquesets.post('http://httpbin.org')   ----测试网站
rquesets.put('')
rquesets.delete('')
rquesets.head('')
rquesets.options('')

3.基本GET请求

response = requests.get('')
print(reponse.text)

4.简单的带参请求

data = {
    'name': 'germey',
    'age': '22',
}

response = requests.get('http://httpbin.org/get', params=data)
print(response.text)

5.解析json
response = requests.get('http://httpbin.org/get')
print(type(response.text))   ---class str
print(response.json())   ---response.json() ===json.loads(response.text)
print(type(response.json()))   ---class dict

6.获取二进制数据

response = requests.get('http://github.com/favicon.icon')
print(response.text)
print(type(response.text))  --- class str
print(response.content)
print(type(response.content))  ---class bytes

with open('favicon.ico','wb') as f:
    f.write(response.content)
    f.close()
    
7.添加headers

headers= {
}

response = requests.get('', headers = headers)

8.基本post请求

import requests

data = {
    'name': 'german',
    'age': '22",
}

response = requests.post('', data=data)

9.响应 Response

response.status_code
response.cookies
response.headers
response.url

10.状态码判断

response = requests.get(http://www.jianshu.com)
exit() if not response.status_code == 200 else print('Request Successfully')

response.status_code == requests.codes.ok/not_found   ---ok/not_found  根据状态码解释填写

11.文件上传
import requests

files = {
    'file': open('favicon.ico','rb')
}
response = requests.post('http://httpbin.org/post', files=files)
print(response.text)

12.获取cookies
response = requests.get('')
for key,value in response.cookies.items():
    print(key + '=' + value)
    
13.会话维持
requests.get('http://httpbin.org/cookies/set/number/12345678')
response = requests.get('http://httpbin.org/cookies')
print(response.text)

s = requests.Session()
s.get('http://httpbin.org/cookies/set/number/12345678')
response = requests.get('http://httpbin.org/cookies')
print(response.text)

14.证书验证

from requests.packages import urlib3
rullib3.disable_warnings()
response = requests.get('',verify=False)  ----忽略证书
-------------------------------------------------------------------------------------------
response = requests.get('',cert=('/path/server.crt','/path/key'))  ---手动添加证书

15.代理设置
proxies={
    'http':'http://user:password@127.0.0.1:9586/',    ---普通代理，此处可以传入用户名密码
}
response = requests.get('', proxies=proxies)
-------------------------------------------------------------------------------------------------
pip3 install 'rquests[socks]'     ---socks代理

proxies={
    'http':'socks5://127.0.0.1:9586/',   
}


16.超时设置
import requests
from requests.exceptions import ReadTimeout

try:
    response = requests.get('', timeout = 1)
except ReadTimeout:
    print('Timeout')
    
17.认证设置
from requests.auth import HTTPBasicAuth

r = requests.get('',auth=HTTPBasicAuth('user','123'))

or

r = requests.get('',auth=('user','123'))

18.异常处理
import requests
from requests.exceptions import ReakTimeout ,HTTPError,RequestException

try:
    response = requests.get('', timeout = 1)
    print(response.status_code)
except ReadTimeout:
    print('Timeout')
except HTTPError:
    print('Http error')
except RequestException:
    print('Error')
    

-----------官方文档 Exceptions 
IOError --RequestException --HTTPError --ConnectionError --ProxyError --SSLError --Timeout --ConnectionTimeout
```





