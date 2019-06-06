# cyphyhouse.rtfd.io
This repository is for automatically generating software documentation website
for [CyPhyHouse project](https://cyphyhouse.github.io/)
on [Read the Docs](https://readthedocs.org/) hosting service.

To read the documentation, please go to https://cyphyhouse.rtfd.io


## Build the website locally

Building this documentation website locally requires **Python 3** and **pip**.
With Python and pip,
please run the command below to install the required Python packages:
```bash
$ pip install -U -r requirements.txt
```

After the packages are installed, simply run following to build the web pages:
```bash
$ make html
```
The generated web pages will be stored under `build\html` folder.