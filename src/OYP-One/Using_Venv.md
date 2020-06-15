### Proper Virtual Environment Usage

#### Why a virtual environment?
In a nutshell a virtual environment is a self-contained python environment and using it ensures that any packages
installed in it are isolated and protected from being unwittingly modified. When you pip-install a python package into
a virtual environment the package is stored in the `.../site-packages` directory relative to the virtual environment;
any interpreter/application running under this virtual environment will have access to this package. This is opposed to
installing the package into the global python environment, where any python interpreter/application running from it is 
slave to the exact version which was installed. If, said application or any of it's dependencies, needed a different
version of a package, upgrading it in the global python environment would be a solution, albeit a poor one.

The simplest and most effective solution is to use virtual environments 
> NEVER install packages into the global python environment...EVER

#### How to create a virtual environment:

Simply use the `venv` utility to create your virtual environment from the global python. The full command is:
`python3 -m venv ./{name-here}`

##### Figure 1
```
~> which python
/usr/bin/python

~> python --version
Python 2.7.16

~> which python3
/Library/Frameworks/Python.framework/Versions/3.8/bin/python3

~> python3 --version
Python 3.8.2

~> python3 -m venv ./.venv

~> ls -a ./
.      ..     .idea  .venv  OYPOne

~> source ./.venv/bin/activate

(.venv) ~> which python
/Users/southa7/PycharmProjects/OYP/.venv/bin/python

(.venv) ~> python --version
Python 3.8.2
```

#### Using your new virtual environment
In [figure 1](#figure-1) you will see that after the virtual environment is created we source a file called `activate`.
This adds the virtual environment's bin directory to your user path, so the `python` command now points to the python
in your virtual environment.

To exit or deactivate the virtual environment, simply use the command `deactivate`

#### Your Turn:
1. Create a virtual environment in your home directory
2. Copy `pip.conf` into your virtual environment directory
3. Activate the virtual environment
4. Run `pip install requests==2.22.0`
5. Run `pip freeze`
6. Deactivate your virtual environment
7. Create another virtual environment in your home directory
8. Copy `pip.conf` into this new virtual environment directory
9. Activate the virtual environment
10. Run `pip install requests`
11. Run `pip freeze`
12. Deactivate your virtual environment

Now compare the outputs of pip freeze and you can see that there are two separate versions
of requests installed independent of each other.