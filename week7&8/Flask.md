# Flask

- [參考資料](https://hackmd.io/@shaoeChen/SyP4YEnef?type=view)

[Toc] 

## 傳址
```python=
from flask import Flask
app = Flask(__name__)

@app.route('/')
def index():
    return 'hello man'
    
if __name__ == '__main__':
    app.debug = True
    app.run()

@app.route('/user/<username>')
def username(username):
    return 'i am ' + username
```
## template
templates資料夾內新增一個html文件並命名為hello.html

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Hello Page</title>
</head>
<body>
    Flask APP
</body>
</html>
```

```python=
from flask import Flask
from flask import render_template

app = Flask(__name__)

@app.route('/')
def index():
    return render_template('abc.html')

if __name__ == '__main__':
    app.debug = True
    app.run()
```

![](https://i.imgur.com/pKHcoeS.png)




![](https://i.imgur.com/3JdACDx.png)

## login POST與GET
```python=
from flask import Flask, request

app = Flask(__name__)

@app.route('/login', methods=['GET', 'POST']) 
def login():
    if request.method == 'POST': 
        return 'Hello ' + request.values['username'] 

    return "<form method='post' action='/login'><input type='text' name='username' />" \
            "</br>" \
           "<button type='submit'>Submit</button></form>"

if __name__ == '__main__':
    app.debug = True
    app.run() 
```

## form action url_for

### login_1.html

``` <!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Hello Page</title>
</head>
<body>
    <form method='post' action={{ url_for('login') }}> 
        <p>
        <input type='text' name='username' />
    </p>
        <p>
        <button type='submit'>Submit</button>
    </p>    
    </form>
</body>
</html>
```

![](https://i.imgur.com/XqgNhsr.png)


## redirect.py
``` python=
from flask import Flask, request, render_template

app = Flask(__name__)

@app.route('/login', methods=['GET', 'POST'])
def login():
    #  利用request取得使用者端傳來的方法為何
    if request.method == 'POST':
                          #  利用request取得表單欄位值
        return 'Hello ' + request.values['username']
    
    #  非POST的時候就會回傳一個空白的模板
    return render_template('login.html')

if __name__ == '__main__':
    app.debug = True
    app.run() 
```
### redirect
![](https://i.imgur.com/xpEOoeh.png)
```python=
from flask import Flask, request, render_template, redirect, url_for

app = Flask(__name__)

@app.route('/loginurl', methods=['GET', 'POST'])
def login():
    if request.method == 'POST':
        return redirect(url_for('hello', username=request.form.get('username')))

    return render_template('login_2.html')

@app.route('/hello/<username>')
def hello(username):
    return render_template('hello_1.html', username=username)

if __name__ == '__main__':
    app.debug = True
    app.run()
```
### hello_1.html
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Hello</title>
</head>
<body>
    hello, {{ username }}, Welcome my homepage!
</body>
</html>
```
## login_2.ht
```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Hello Page</title>
</head>
<body>
    <form method='post' action={{ url_for('login') }}>
        <p>
        <input type='text' name='username' />
    </p>
        <p>
        <button type='submit'>Submit</button>
    </p>
    </form>
</body>
</html>
```
## Flash
- [官方 flash文件](https://flask.palletsprojects.com/en/1.1.x/patterns/flashing/)
![](https://i.imgur.com/QqN1iQQ.png)

## 繼承
- base.html
```
<!DOCTYPE html>
<html lang="en">    
<head>
    {% block head %}
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>{% block title%}{% endblock title%} -titleBlock</title>
    {% endblock head %}
</head>
<body>
    <h1>Welcome to the test HTML</h1>
    <h2>大家都要用的就不要用block處理</h2>
    <h3>block的區塊是提供調整的部位</h3>
    {% with messages = get_flashed_messages() %}
    {% if messages %}
    <ul class="flash">
        {% for message in messages %}
        <li>{{ message }}</li>
        {% endfor %}
    </ul>
    {% endif %}
    {% endwith%}
    <div class="content">
        {% block content %}
        {% endblock content %}        
    </div>
</body>
</html>
```
- login.html
```
{% extends "base.html" %}
{% block title %}Login{% endblock title%}
{% block content%}
<form method='post' action={{ url_for('login') }}>
        <p>
        <input type='text' name='username'>
    </p>
        <p>
        <input type="text" name="password">
    </p>
        <p>
        <button type='submit'>Submit</button>
    </p>
</form>
{% endblock content%}
```
- python
```python=
from flask import Flask, request, render_template, redirect, url_for

app = Flask(__name__)


@app.route('/login', methods=['GET', 'POST'])
def login():
    if request.method == 'POST':
        return redirect(url_for('hello', username=request.form.get('username')))

    return render_template('login.html')


@app.route('/hello/<username>')
def hello(username):
    return render_template('hello.html', username=username)


if __name__ == '__main__':
    app.debug = True
    app.run()
```
## 樣板繼承加入JS
- 使用{{ super() }}
```
{% extends "base.html" %}
{% block head %}
{{ super() }}
<script>var a=99;</script>
{% endblock head %}
{% block title %}Login{% endblock title %}
{% block content%}
<form method='post' action={{ url_for('login') }}>
        <p>
        <input type='text' name='username'>
    </p>
        <p>
        <input type="text" name="password">
    </p>
        <p>
        <button type='submit'>Submit</button>
    </p>
</form>
{% endblock content%}
```

## 　Flask_SQLAlchemy
[參考官方文獻](https://flask-sqlalchemy.palletsprojects.com/en/2.x/quickstart/#a-minimal-application)
- model.py
```python=
from flask import Flask
from flask_sqlalchemy import SQLAlchemy
import os
app = Flask(__name__)
#  新版本的部份預設為none，會有異常，再設置True即可。
app.config['SQLALCHEMY_TRACK_MODIFICATIONS'] = True
app.config['SQLALCHEMY_DATABASE_URI'] = 'sqlite:///:memory:' 
db = SQLAlchemy(app)
class User(db.Model):
    __tablename__ = 'Users'
    id = db.Column(db.Integer, primary_key=True)
    username = db.Column(db.String(80), unique=True, nullable=False)
    email = db.Column(db.String(120), unique=True, nullable=False)

    def __init__(self, username, email):
        self.username = username
        self.email = email

    def __repr__(self):
        return '<User %r>' % self.username
```
![](https://i.imgur.com/Bvwz56r.png)
![](https://i.imgur.com/grhyVk9.png)





