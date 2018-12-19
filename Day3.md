# Day3

## 1. Dictionary

Dictionary 는 ```key```와 ```value```가 짝지어져 있다.

key는  ```string``` , ```integer```, ```boolean``` 이 가능하다. ```list```혹은 ```dictionary```는 안돤다.

value에는 모든 자료형이 가능하다. ``list`` 혹은 ```dictionary```는 가능하다.

1) 딕셔너리 만들기

``` phonebook["분식집"] = "031"``` 

2)내용추가하기

3) 딕셔너리

4)딕셔너리 반복문 활용하기

```	#기본 활용```

``` python
for key in phonebook.items():
    print(key,value)

for value in phonebook.valueS():
    print(value)
    
for 
```

 	 

[연습문제](www.zzu.l)

```python  
total_score=0
length=0
for person_score in score.values():
    for individual_score in person_score.values():
        total_score += individual_score
```





## 텔레그램  API 활용하기

사전 준비사항 : @botfather를 통해서 봇을 만들어서 토큰 정보를 기록한다.



### 0. 봇 정보 가져오기

``` f"https://api.telegram.org/bot{token}/getME" ```

```python 
import requests
token = "insert your token here"
url = f"https://api.telegram.org/bot{token}/getME"
response = requests.get(url)
```



### 1. 메세지 보내기

1)  User의 ```id```정보를 가져와야 함.

```python
https://api.telegram.org/bot{token}/getUpdates
    
```

```python
import requests
# 1. 사용자 정보 가져오기 위한 요청
token = "토큰"
url = f"https://api.telegram.org/bot{token}/getUpdates"
response = requests.get(url).json()

# 2. 
user_id = response["result"][0]["result"][0]["message"]["from"]["id"]
msg = "안녕?"

send_url = f"https://api.telegram.org/bot{token}/sendMessage?text={msg}&chat_id={user_id}"
requests.get(url)

```









