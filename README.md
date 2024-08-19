# Python Sample Web App

A simple [Flask](https://flask.palletsprojects.com/)-powered Python sample web app, learnt from: https://realpython.com/flask-project/.

## How to run

1. Clone it back:

```sh
$ git clone https://github.com/brightzheng100/python-example.git
```

2. Create a "virtual env" to host the app:
 
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


3. Init the app:

```sh
(app) $ python -m pip install Flask
```

4. Start it up:

```sh
(app) $ python -m flask --app board run --port 8000 --debug
```

Now you can access it in browser through: http://localhost:8000/

> Note: `CTRL + C` to stop and quit the app.
