# NOT FULLY TESTED: How to install from source on PythonAnywhere

## TODO:
* Explain what this does ./py4web.py set_password
* Is this specific enough? 
  + * Choose **Python 3.8** or **Python 3.7**.
* I can only install with the `--user` option like this:
  + python3 -m pip install --user -r requirements.txt

  And not as shown in the docs:
  + python3 -m pip install  -r requirements.txt

## Download Git to your own machine

This tutorial requires that you have the [Git] command-line utility

* Download Git from [git-scm.com](https://git-scm.com/).

It helps but isn't required that you follow its excellent tutorial.

* [Create a PythonAnywhere account](create-pythonanywhere-account.md)

## Go to the PythonAnywhere dashboard

Let's make sure we're on the same page, which should the the dashboard.

* Choose the [PythonAnywhere logo](https://www.pythonanywhere.com/) at the top of the page to navigate to the PythonAnywhere dashboard.

You'll see a navigation menu near the top of the page that says **Dashboard  Consoles  Files  Web  Tasks  Databases**.

## Go to the WebApps page and create a new web app

On the navigation bar near the top of the page that says **Dashboard  Consoles  Files  Web  Tasks  Databases** choose **Web**

* Choose **Add a new web app**.

* A dialog appears called  **Create a new web app**

You're informed that PythonAnywhere is creating a URL for your site and displays that URL.

* Choose **Next**.

### Choose the Flask framework

The **Select a Python Web framework**  dialog appears, showing a list of frameworks like web2py, Django, Flask, and so on.

Currently there's no built-in support for py4web, but py4web is based partly on Flask. So:

* Choose **Flask** from the list.

You're asked to select a Python version.

* Choose **Python 3.8** or **Python 3.7**.

The **Quickstart new Flask Project** dialog appears. You're asked to give the location where a `flask_app.py` file will be generated. 
It looks something like this, where `XXX` would be the username you created on signup. You'll need to change it.

**Path**  

```bash
/home/XXX/mysite/flask_app.py
```

* Replace the `mysite` portion with `py4web`. The whole thing would look like this, where `XXX` is used in place of your account name. For example:

```bash
/home/XXX/py4web/flask_app.py
```

* Choose **Next**.

### Reload your web app

You're returned to the **Web** page

There is now a **Configuration** section with the name of your URL, and a big green **Reload** button with your URL on it.

* Choose the **Reload XXX.pythonanywhere.com** button, where XXX is used in place of your account name.

A wait icon appears for a few seconds, then the page returns to its previous state. You're finally ready to install py4web.

## Installing py4web from source on pythonanywhere

One of the distinct features of py4web is that it is nothing more than a Python program. py4web apps are nothing more than a simple
directory tree structure with a few files inside an applications subdirectory. This section shows how to clone the py4web repo
from GitHub. It uses the Bash command line console supplied with PythonAnywhere.

### Start the bash console

* From the **Dashboard  Consoles  Files  Web  Tasks  Databases** navigation menu choose **Consoles**.

You'll see **Start a new Console**.

* Next to Other, choose **Bash**.

After a few seconds, the Bash prompt appears. It looks roughly like this: `~ $`.


## Clone the GitHub repo

The next step is to obtain a copy of the py4web distribution. The following copies the latest
supported major release into its own directory.

* Enter `git clone https://github.com/web2py/py4web.git` at the prompt:

```bash
$ git clone https://github.com/web2py/py4web.git
```

A list of progress messages scrolls down. It looks something like this, but longer:

```
Cloning into 'py4web'...
remote: Enumerating objects: 167, done.
remote: Counting objects: 100% (167/167), done.
...
Checking out files: 100% (660/660), done.
04:21 ~ $ 
```
The result is a `py4web` subdirectory in your root directory containing the py4web source treee.

### Change to the py4web directory and install using pip

Make py4web the current directory:

```bash
$ cd py4web
```

* Enter **python3 -m pip install -r requirements.txt** to install using pip:

```bash
$ python3 -m pip install -r requirements.txt
```

### Setup py4web itself

Now configure py4web:

```bash
$ ./py4web.py setup apps
$ ./py4web.py set_password
```

## Change your site's working directory

* From the **Dashboard  Consoles  Files  Web  Tasks  Databases** navigation menu choose **Web**.

* Scroll down to the section headed **Code**, which shows **Source Code**, **Working Directory**, and other information.

### Make your py4web folder both the source code and working directory

* Click the URL next to **Source Code**. It is made editable. Make sure the end contains your URL followed by `/py4web`. Replace `XXX`
in the following example with your project URL:

/home/XXX/py4web

* Do the same for **Working directory**.

### Update your WSGI configuration file 

The WSGI configuration needs your project's home directory updated from its default value. Just under **Source code** and **Working directory** you'll see **WSGI configuration file**. You can open up a built-in editor
for it simply by clicking.

* Click the link for **WSGI configuration file** and your WSGI configuration file appears in an editor.

You'll see something like this, with your username in place of `XXX`:

```
project_home = '/home/XXX/mysite'
```

* Change it to your py4web apps folder name like this, replacing `XXX` with your username. Make sure it all
stays within the quote marks:

```
project_home = '/home/XXX/py4web/apps'
```

* At the top of the page choose **Save** to preserve your chnanges.
