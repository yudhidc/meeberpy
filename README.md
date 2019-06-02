# Meeber Python
[![Build Status](https://travis-ci.com/derymukti/meeberpy.svg?branch=master)](https://travis-ci.com/derymukti/meeberpy)
[![codecov](https://codecov.io/gh/derymukti/meeberpy/branch/master/graph/badge.svg)](https://codecov.io/gh/derymukti/meeberpy)

Meeber Python is skeleton python with flask.

  - PostgreSQL
  - Python 2.7
  - ORM (Sqlalchemy)
  - pip
 
### Installation

Meeber Python requires [Python2.7](https://www.python.org/downloads/release/python-2716/) to run.

Config and run.
for configuration you can edit in file "config.json"

```sh
$ cd meeberpy
$ pip install -r requirements.txt
$ python main.py migrate
$ python main.py seed
$ python main.py run
```

### How To Create Controller?

Meeber python is simple architecture folder.

```sh
$ python main.py create:controllers -n testing
```
after run this command you will found 'testing' folder in controllers.
and new line code in file controllers/__init__.py
```python
---
from testing.router import testing
app.register_blueprint(testing)
---
```
example for testing controller:

| File | Description |
| ------ | ------ |
| controllers/__init__.py | this a public routing, u can register blueprint here |
| controllers/testing/__init__.py | u can import local router here |
| controllers/testing/router.py | this a local router , u can add more endpoint here |
| controllers/testing/modules/__init__.py | this a modules for use in your endpoint, u can add more function in here |


License
----

MIT