# Flask

* [공홈](http://flask.pocoo.org/)

## 1. 설치하기 

```$ pip install flask```

## 2. 시작하기

```python
#hello.py
from flask imprt Flask
app = Flask(__name__)

# "/" 는 루트 디렉토리를 뜻한다.
@app.route("/")
def hello():
    return "Hello Flask"

```

서버 실행하기

```python
$ FLASK_APP=hello.py flask run
```

크롬으로 ```http://localhost:500```, ```http://197.0.0.1:5000```을 열어본다!

```python
@app.route("/ssafy")
def ssafy():
    return "Hello ssafy!"
#http://localhost:5000/ssafy
```

## 3. Variable Routing

+ url에 있는 정보를 변수로 활용하는 법

```python
@app.route("/greeting/<string:name>")
def greeting(name): #반드시 위에 string:name과 같은 인자로
    return f"{name}, Hi?"

#http://localhost:5000/greeting/Ashley
# [Ashley, Hi?] 출력이 예상

```

## 4. render_template

+ ```render_template```를 활용하기 위해서는 ```import```해줘야 함~!

```python
#hello.py
from flask import Flask, render_template

@app.route("/")
def hello():
    return render_template("index.html")
```

```html
<!-- templates/index.html -->
<html>
    <head>
        
        
    </head>
    <body>
        Hi There!
    </body>
</html>
```

+ ```render_template```을 사용하면, html파일에서의 변수, 조건, 반복문 등을 활용할 수 있다.
+ ```jinja2```라고 하는 템플릿 엔진을 활용하고 있기 때문이다.
+ 기본적으로 html파일은 ```templates/``` 폴더 안에 만들어야 한다.

```python
@app.route('/dinner')
def dinner():
    menu = "신전떡볶이"
    return render_template("dinner.html", menu=menu)
```

```html
<!-- templates/dinner.html-->
{{menu}} <!--  출력을 원할 경우 {{}}을 활용한다. -->
{% if ___ %} <!--  제어문은 {% %}를 활용한다. -->
	<h>참이면</h>
	<h>보이지롱</h>
{% else %}
	<h>거짓이면</h>
	<h>보이지롱</h>
{% endif %}
{% for i in menus %}
	<p>
        {{i}}
	</p>
{% endfor %}
```

### 주의사항

token은 반드시 외부에 공개되면 안된다.

따라서, 환경 변수를 활용하여 정보를 전달하자.

```python
$ vi ~/.bash_profile
export TELEGRAM_TOKEN = "inset your token"
```

```python
import os
token = os.getenv("TELEGRAM_TOKEN")
```

