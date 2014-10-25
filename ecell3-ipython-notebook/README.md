Dockerized E-Cell3 with IPython Notebook
========================================

Docker container for the E-Cell3 with IPython notebook (single user).

## Quickstart

Assuming you have docker installed, run this to start up a notebook server over HTTPS.

```
docker run -d -p 80:8888 naito/ecell3-ipython-notebook
```

You'll now be able to access your notebook at http://<docker host ip>.

