# DS_project
You found these great Docker containers for data science, but they are a hassle to use? These scripts make it easy to start, stop and destroy these containers.

This is a companion-repository for either the [Original Jupyter Docker Stacks](https://github.com/jupyter/docker-stacks) or the [GPU-enabled Docker Stacks](https://github.com/OleMussmann/docker-stacks).

## 🎬 Getting started

1. Clone this repository.
```
git clone git@github.com:OleMussmann/DS_project.git
```

2. Rename the folder to your liking, `cd` into folder.
```
mv DS_project MyDataScienceProject && cd MyDataScienceProject
```

3. Edit the `.env` file and choose a docker container for the `NOTEBOOK` variable, for example:
```
NOTEBOOK=isbjornlabs/fastai-notebook-cuda10.1:latest
```

4. For quick testing, just use the `workdir` folder to preserve your scripts and data. For a serious project, please consider a proper project structure like [Cookiecutter Data Science](https://drivendata.github.io/cookiecutter-data-science/#getting-started) within the `workdir`.

5. Use the scripts below to start, stop and destroy your data science environments.

## 📑 Scripts

[`dc`](dc) is a (very thin) wrapper around docker-compose, use it just the same. [`enter_container`](enter_container) starts a `bash`-shell in an existing container, if you prefer to work without Jupyter notebooks.

### Jupyter Notebook

| action           | command    |
|------------------|------------|
| start container  | `./dc up`  |
| stop container   | `CTRL-C`   |
| remove container | `./dc down`|

### Bash Shell

| action           | command                                 |
|------------------|-----------------------------------------|
| start container  | `./dc -f docker-compose-bash.yml up`    |
| enter container  | different terminal: `./enter_container` |
| exit container   | different terminal: `CTRL-D`            |
| stop container   | `CTRL-C`                                |
| remove container | `./dc -f docker-compose-bash.yml down`  |

### Customization
Use environment variables to quickly override settings without editing `.env`. Starting a different notebook `jupyter/tensorflow-notebook` on port `1234`:

```
NOTEBOOK=jupyter/tensorflow-notebook PORT=1234 ./dc up
```

