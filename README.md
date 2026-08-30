# Python-
Python project 1
from flask import Flask

app = Flask(__name__)

@app.route("/")
def home():
    return "<h1>Hello Naksh! 👋</h1><p>My website is running with Python!</p>"

app.run()
