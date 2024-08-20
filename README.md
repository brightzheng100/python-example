# Python Sample Web App

A simple [Flask](https://flask.palletsprojects.com/)-powered Python sample web app, learnt from: https://realpython.com/flask-project/.

## How to run

### 1. Clone it back

```sh
$ git clone https://github.com/brightzheng100/python-example.git
$ cd python-example
```

### 2. Install Python if you haven't

Well, I'd assume you've installed Python3.
If you haven't, you may do something like this when in RHEL:

```sh
$ sudo yum install -y epel-release
$ sudo yum install -y python38 python38-pip
```

And this is what I tested this app:

```sh
$ python3 --version
Python 3.8.17
```

### 3. Create a "virtual env" to host the app

 
If you're with `venv` -- this is my case for simplicity:

```sh
$ python3 -m venv .venv --prompt app
$ source .venv/bin/activate
```

> Note: to deactivate the venv, simply run this: `deactivate`.

Or, if you're with `conda`:

```sh
$ conda create -n python-example python=3.8
$ conda activate python-example
```

> Note: to deactivate the `conda` env, simply run this: `conda deactivate`.


### 4. Install the required package

We have only one package needed, which is `Flask`:

```sh
(app) $ python -m pip install Flask
```

### 5. Run it

Run it to listen on port `8080`:

```sh
(app) $ python -m flask --app board run --port 8080
```


Or, listen on port `8080` but with all IPs:

```sh
(app) $ python -m flask --app board run --host=0.0.0.0 --port 8080
```


Or, furthermore, if you want to run it with `uWSGI`, which is a fast, compiled server suite with extensive configuration and capabilities beyond a basic server, do this -- refer to the `uWSGI` doc [here](https://uwsgi-docs.readthedocs.io/en/latest/):

```sh
(app) $ pip install pyuwsgi
(app) $ uwsgi --http 0.0.0.0:8080 --master -p 4 -w wsgi:app
```


Or, you may want to run it at backend quietly:

```sh
$ nohup bash -c "python -m flask --app board run --host=0.0.0.0 --port 8080" &> app.out & echo $! > app.pid
```

Then you can:
- Tail the app's logs by: `tail -f app.out`.
- Kill it by: `kill $(cat app.pid)`.

Anyway, now you can access it in browser through: http://localhost:8080/

> Note: `CTRL + C` to stop and quit the app.


## When monitored by IBM Instana

IBM Instana offers great support for Python apps without any code changes.

The typical steps might look like:
1. Install the Instana sensor into your app, which will be automatically handled with webhook when you're with Kubernetes/OpenShift: `pip install git+https://github.com/instana/python-sensor@v2.5.2`.
2. Export one necessary variable, which can be at global system or process level: `AUTOWRAPT_BOOTSTRAP=instana`.
3. Optionally, define a friendly service name, which will be discovered and displayed on UI, say `INSTANA_SERVICE_NAME=my-simple-python-app`.
4. Optionally, enable `INSTANA_DEBUG=true` to output verbose instrumentation / tracing info, which helps when you're trying to learn more.

So the run command may look like this: 

```sh
$ nohup bash -c "AUTOWRAPT_BOOTSTRAP=instana INSTANA_SERVICE_NAME=my-cool-python-app INSTANA_DEBUG=true python -m flask --app board run --host=0.0.0.0 --port 8080" &> app.out & echo $! > app.pid
```
