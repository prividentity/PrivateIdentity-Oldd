

> # Installation[](https://clear-demo.s3.us-east-2.amazonaws.com/privateid-sdkdocs/installation.html#installation "Permalink to this headline")

## Python Version[](https://clear-demo.s3.us-east-2.amazonaws.com/privateid-sdkdocs/installation.html#python-version "Permalink to this headline")

We recommend using the latest version of Python. PrivateID supports Python 3.6 and newer.

## Dependencies[](https://clear-demo.s3.us-east-2.amazonaws.com/privateid-sdkdocs/installation.html#dependencies "Permalink to this headline")

PrivateID have dependencies on numpy, scipy and Pillow for image processing. These distributions will be installed automatically. PrivateID will detect and use them if already installed.

-   [Numpy](https://pypi.org/project/numpy/)  provides functions for array wise image manipulation.
    
-   [Pillow](https://pypi.org/project/Pillow/)  provides functionalities for reading the Image and converting to required formats.
    
-   [Scipy](https://pypi.org/project/scipy/)  provides a faster, more efficient method for comparison of distances and supports shared library functionalities.
    

## Virtual environments[¶](https://clear-demo.s3.us-east-2.amazonaws.com/privateid-sdkdocs/installation.html#virtual-environments "Permalink to this headline")

Use a virtual environment to manage the dependencies for your project, both in development and in production.

What problem does a virtual environment solve? The more Python projects you have, the more likely it is that you need to work with different versions of Python libraries, or even Python itself. Newer versions of libraries for one project can break compatibility in another project.

Virtual environments are independent groups of Python libraries, one for each project. Packages installed for one project will not affect other projects or the operating system’s packages.

Python comes bundled with the  `venv`  module to create virtual environments.

### Create an environment[](https://clear-demo.s3.us-east-2.amazonaws.com/privateid-sdkdocs/installation.html#create-an-environment "Permalink to this headline")

Create a project folder and a  `venv`  folder within:

mkdir myproject
cd myproject
python3 -m venv venv

On Windows:

py -3 -m venv venv

### Activate the environment[](https://clear-demo.s3.us-east-2.amazonaws.com/privateid-sdkdocs/installation.html#activate-the-environment "Permalink to this headline")

Before you work on your project, activate the corresponding environment:

. venv/bin/activate

On Windows:

venv\Scripts\activate

Your shell prompt will change to show the name of the activated environment.

## Install PrivateID[](https://clear-demo.s3.us-east-2.amazonaws.com/privateid-sdkdocs/installation.html#install-privateid "Permalink to this headline")

Within the activated environment, use the following command to install Werkzeug:

pip3 install https://clear-demo.s3.us-east-2.amazonaws.com/privateid/privateid-1.1.0-py3-none-any.whl