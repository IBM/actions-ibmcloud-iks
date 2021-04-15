# Use GitHub Actions to Deploy to IBM Kubernetes Service

This repo contains a sample GitHub Action for deploying an application to IBM Kubernetes Service (IKS). The application is a simple HelloWorld app using Python and Flask framework.

## Deploy with GitHub Actions

1. If you'd like to use the file yourself fork the repo and open [.github/workflows/iks.yml](.github/workflows/iks.yml), you'll need to update a few environment variables.
1. Add your own IKS cluster name, image name, and deployment name.
1. In your GitHub repository settings create two secrets, `ICR_NAMESPACE` and `IBM_CLOUD_API_KEY`.

Get a new IBM Cloud API key from the [IAM settings](https://cloud.ibm.com/iam/apikeys).

By default, a new version of the app will be deployed on every `push`, you can change this to on `release`.

## Run locally

### With python

System Requirements: [Git](http://www.git-scm.com), [Python 3.8.0](https://www.python.org/downloads/)

```bash
# Check dependencies
$ git --version
git version 2.23.0

$ python --version
Python 3.8.0

$ pip --version # pip comes as a part of python install
pip 20.0.2 from /usr/local/lib/python3.8/site-packages/pip (python 3.8)

# Clone the sourcecode
$ git clone <repo url>
$ cd <project dir>

# Install project dependencies
$ pip install -r requirements.txt

# Run the application
$ PORT=5001 python src/app.py

# Check application
$ curl http://localhost:5001/debug
# (or)
# In Browser visit -> http://localhost:5001/debug/ui
```

### With Docker

```bash
$ docker build -f Dockerfile -t hello-python:latest .

$ docker run -it -p 5001:5001 --name hello_python hello-python:latest

# Docker Docs: https://docs.docker.com/
# Docker Reference: https://docs.docker.com/reference/
```

### With Docker Compose

```bash
$ docker-compose up hello_py_devl && docker-compose rm -fsv

# For additional instruction please see notes at the bottom
# of docker-compose.yml file in the app root directory.

# Docker compose docs: https://docs.docker.com/compose/
```
