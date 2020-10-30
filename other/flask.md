# Flask cheatsheet

## Table of contents

- [Docs](#docs)
- [Import](#import)
- [Simple decorators](#simple-decorators)

### Docs
- [Flask official documentation](https://flask.palletsprojects.com)
- [Запуск Flask приложения c uWSGI, virtualenv и nginx](https://the-bosha.ru/2017/01/04/zapusk-flask-prilozheniia-c-uwsgi-virtualenv-i-nginx/)

### Import

```
from flask import Flask
from markupsafe import escape
```

### Simple decorators

Func usage:
```
@app.route('/blabla/', methods=['GET', 'POST'])
def foo():
    return 'Bla bla page'
```

| Desc                | Syntax                               |
| ---                 | ---                                  |
| Just path           | `@app.route("/blabla")`              |
| Path with given var | `@app.route('/user/<username>')`     |
| Var as `int`        | `@app.route('/post/<int:post_id>')`  |
| Var as a subpath    | `@app.route('/path/<path:subpath>')` |
