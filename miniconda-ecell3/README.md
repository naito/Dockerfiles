miniconda-ecell3
================

Build
-----

* Build the Dockerfile to make a Docker image file "ecell3".
```bash
$ docker build -t ecell3 .
```

Usage
-----

* Run Docker image file "ecell3".
```bash
$ docker run -it -p 8888:8888 ecell3
```

* Run E-Cell3 Jupyter Notebook.
```bash
(base) root@ff45e8a22073:/# ecell3-notebook
[TerminalIPythonApp] WARNING | Subcommand `ipython notebook` is deprecated and will be removed in future versions.
[TerminalIPythonApp] WARNING | You likely want to use `jupyter notebook` in the future
[I 07:39:05.931 NotebookApp] Writing notebook server cookie secret to /root/.local/share/jupyter/runtime/notebook_cookie_secret
[W 07:39:05.952 NotebookApp] WARNING: The notebook server is listening on all IP addresses and not using encryption. This is not recommended.
[I 07:39:05.962 NotebookApp] Serving notebooks from local directory: /notebooks
[I 07:39:05.962 NotebookApp] 0 active kernels
[I 07:39:05.962 NotebookApp] The Jupyter Notebook is running at: http://[all ip addresses on your system]:8888/?token=4aa99a77f52651e466fc39a53e7e680768652da48086781d
[I 07:39:05.962 NotebookApp] Use Control-C to stop this server and shut down all kernels (twice to skip confirmation).
[C 07:39:05.963 NotebookApp]

    Copy/paste this URL into your browser when you connect for the first time,
    to login with a token:
        http://localhost:8888/?token=4aa99a77f52651e466fc39a53e7e680768652da48086781d
```

* Copy the URL in the last line, and paste it your web browser.
