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
##### this will be creating new endpoint "hostname:port/testing"

after run this command you will found 'testing' folder in controllers.
and new line code in file controllers/`__init__.py`
```python

from testing.router import testing
app.register_blueprint(testing)

```
example for testing controller:

| File | Description |
| ------ | ------ |
| controllers/`__init__.py` | this a public routing, u can register blueprint here |
| controllers/testing/`__init__.py` | u can import local router here |
| controllers/testing/`router.py` | this a local router , u can add more entities here |
| controllers/testing/modules/`__init__.py` | this a modules for use in your endpoint, u can add more function in here |

# How to create Entities?
1. open file controller/yourcontroller/modules/`__init__.py` and add this to end of file
    ```python
    def get():
        return "hello?"
    ```
2. open file controller/yourcontroller/router.py and add this to end of file
    ```python
    @yourcontroller.route('/new_entities',methods=['GET'])
    def get_data():
        return get()
    ```
    this will be creating new entities like "hostname:port/yourcontroller/new_entities" with GET method  
 - __get()__ is import from modules/`__init__.py`  
# How to return in json type?
1. cek your `__init__.py` file in `modules` make sure this import 
    ```python
    from manager.json_response import response
    ```
2. add this in function to return. ex:
    ```python
    def get():
        json_data={"title":"this title","description":"this description"}
        return response(data=json_data,code=200,messages="success")
    ```
    
    this will be return
    ```json
    {
        "meta": {
            "message": "success",
            "code": 200
        },
        "data": {
            "title":"this title",
            "description":"this description"
            }
    }
    ```
    | Name | Type | Description |
    | ------| ------ | ------ |
    | code | INT |this is code for header response and status |
    | message | String | message for response |
    | data | String, Array, Object | data for return |
