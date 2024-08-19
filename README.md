# Python Sample Web App

A simple [Flask](https://flask.palletsprojects.com/)-powered Python sample web app, learnt from: https://realpython.com/flask-project/.

## How to run

1. Clone it back

```sh
$ git clone https://github.com/brightzheng100/python-example.git
$ cd python-example
```

2. Install Python if you haven't

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

3. Create a "virtual env" to host the app:

 
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


4. Init the app:

```sh
(app) $ python -m pip install Flask
```

1. Run it:

Run it to listen on port `8080`:

```sh
(app) $ python -m flask --app board run --port 8080
```

Or listen to all IPs:

```sh
(app) $ python -m flask --app board run --host=0.0.0.0 --port 8080
```

Now you can access it in browser through: http://localhost:8080/

> Note: `CTRL + C` to stop and quit the app.
