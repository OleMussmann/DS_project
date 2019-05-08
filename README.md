# DS_project
You found these great Docker containers for data science, but they are a hassle to use? These scripts make it easy to start, stop and destroy these containers.

This is a companion-repository for either the [Original Jupyter Docker Stacks](https://github.com/jupyter/docker-stacks) or the [GPU-enabled Docker Stacks](https://github.com/OleMussmann/docker-stacks).

## 🎬 Getting started

1. Clone this repository.
```
git clone git@github.com:OleMussmann/DS_project.git
```

2. Rename the folder to your liking.
```
mv DS_project MyDataScienceProject
```

3. Edit the `.env` file, choose a docker container for the `NOTEBOOK` variable, for example:
```
NOTEBOOK=isbjornlabs/fastai-notebook-cuda10.1:latest
```

4. For quick testing, just use the `workdir` folder to preserve your scripts and data. For a serious project, please use a proper project structure like [Cookiecutter Data Science](https://drivendata.github.io/cookiecutter-data-science/#getting-started) within the `workdir`.

## 📑 Scripts

`d-c` is a (very thin) wrapper around docker-compose, use it just the same.

### Jupyter Notebook

|
|------------------|-------------|
| start container  | `./d-c up`  |
| stop container   | `CTRL-C`    |
| remove container | `./d-c down`|

### Bash Shell

|
|------------------|-------------|
| start container  | `./d-c -f docker-compose-bash.yml up`  |
| enter container  | different terminal: `./enter`  |
| exit container   | different terminal: `CTRL-D`  |
| stop container   | `CTRL-C`    |
| remove container | `./d-c -f docker-compose-bash.yml down`|

### Customization
Use environment variables to quickly override settings without editing `.env`. For example starting a different notebook `jupyter/tensorflow-notebook` on port `1234`:

```
NOTEBOOK=jupyter/tensorflow-notebook PORT=1234 ./d-c up
```

