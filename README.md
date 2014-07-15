bild3
======

bild3 (formerly malid3) is a web app designed in Python using the Flask framework for manually tracking changes made to music files and easy access to the Billboard Hot 100 through an [unofficial API designed by guoguo12](https://github.com/guoguo12/billboard-charts) without the unnecessary pictures/articles. The general layout and functions were based off of the [Flaskr tutorial](http://flask.pocoo.org/docs/tutorial/introduction/), with extra columns added to the database and JQuery implementation to allow for easy navigation among options.

It can be seen at http://bild3.herokuapp.com/. The database resets after an hour of inactivity since a free Heroku account allows for only one dyno.

![malid3_add_overhaul](https://cloud.githubusercontent.com/assets/6787907/3452244/130645e8-01ae-11e4-823f-2621c7742754.png)
![malid3_add_overhaul2](https://cloud.githubusercontent.com/assets/6787907/3452243/1305fd22-01ae-11e4-9284-ed279f040bae.png)

Quickstart
======

If you already have git, pip, and virtualenv:
```sh
$ git clone https://github.com/brycematsuda/bild3.git
$ cd bild3
$ virtualenv venv
$ . venv/bin/activate
(venv)$ pip install -r requirements.txt
```

To run:
```sh
(venv)$ python bild3.py
```
or:
```sh
(venv)$ foreman start
```
and go to http://localhost:5000 in your browser. 

To deploy to Heroku:
```sh
(venv)$ heroku create
(venv)$ git push heroku master 
(venv)$ heroku config:set SECRET_KEY='development_key' USERNAME=admin PASSWORD=default
```
and go to the URL given in the shell output. 

The login info for now is the default set by the tutorial (user: admin / password: default).

Project Setup
======
#### Download this repository from github.
```sh
$ git clone https://github.com/brycematsuda/bild3.git
```
If you don't have git,
```sh
$ sudo apt-get install git
```
For more information, see https://help.github.com/articles/set-up-git .

#### Install Pip
Install pip, which is a [package management](http://en.wikipedia.org/wiki/Package_management_system) system for Python, similar to gem or npm for Ruby and Node, respectively. 

```sh
$ easy_install pip
```

#### Now install [virtualenv](https://pypi.python.org/pypi/virtualenv) to create an isolated environment for development. 

This is standard practice. Always, always, ALWAYS use virtualenv. If you don't, you will eventually run into problems with compatibility between different dependencies. Just do it.

```sh 
$ pip install virtualenv
```

#### Activate your virtualenv.

```sh
$ virtualenv venv --distribute --no-site-packages
$ source venv/bin/activate
```

> You know that you are in a virtual env, as the actual "env" is now show before the $ in your terminal - (env). To exit the virtual environment, use the command `deactivate`, then you can reactivate by navigating back to the directory and running - `source env/bin/activate`.

Note: --no-site-packages may not be needed, you will get a message saying
"The --no-site-packages flag is deprecated; it is now the default behavior."

Note: You should NOT have spaces in the path to this directory! Otherwise you
may encounter errors such as
```sh
Error [Errno 2] No such file or directory while executing command ".
```

Deploy on Heroku
=======
If you've never used Heroku before, go to http://heroku.com and create an account.

We need to install the heroku toolchain and then connect to it:
https://toolbelt.heroku.com/
For ubuntu, this is just:
```sh
$ wget -qO- https://toolbelt.heroku.com/install-ubuntu.sh | sh 
```

https://devcenter.heroku.com/articles/getting-started-with-python
```sh
$ heroku login
```

We create a new heroku app, commit our files to it, and then set the
configuration variables.

```sh
(venv)$ heroku create --stack cedar
(venv)$ git commit heroku master
(venv)$ heroku config:set SECRET_KEY='development key' USERNAME=admin PASSWORD=default
```
Note: If you don't set the config variables, the app will still work, but it 
will be pretty useless since you can't login (it will flash a message, "Invalid
username", without crashing the app.


Remove from Heroku
=======
```sh
$ heroku info
=== safe-hollows-3028
Git URL:       git@heroku.com:safe-hollows-3028.git
Owner Email:   xxx@example.com 
Region:        us
Repo Size:     232k
Slug Size:     31M
Stack:         cedar
Web URL:       http://safe-hollows-3028.herokuapp.com/
$ heroku apps:destroy safe-hollows-3028
```

Credits
=======
- Most of the setup documentation was taken from [flaskr-tdd](https://github.com/mjhea0/flaskr-tdd) and [WTFisThisRegister](https://github.com/nouyang/WTFisThisRegister).
- [guoguo12](http://github.com/guoguo12) for the unofficial Billboard API
- The Billboard charts are owned by Prometheus Global Media LLC. See Billboard.com's [Terms of Use](http://www.billboard.com/terms-of-use) for more information.
