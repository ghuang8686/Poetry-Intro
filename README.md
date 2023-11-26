# Poetry-Intro

Poetry as a Python package development tool is very portable and powerful. It also provides a solution to run the Spark in the local virtual environment. Here I list the basic Poetry commands.

`pip install poetry`: install poetry package on Python

`poetry init`:  if it is your first time to build poetry packge on your existing project, i.e., there is no pyproject.toml file in your package.

`poetry new poetry-demo`: this will create an empty directory called `poetry-demo` with pyproject.toml file.

```
python -m venv .venv
Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope Process
.\.venv\Scripts\Activate
```
This activate the virtual environment. Some system doesn't allow the virtual environment activation by default, `Set-ExecutionPolicy -ExecutionPolicy Bypass -Scope Process` can activate the virtual environment for one-time.

```
poetry install # install all the packages from poetry.lock file
poetry env info # check the virtual environment
# use the Virtualenv.Executable path as the python interpreter
poetry shell # Enter the shell (create a nested shell).
```

`poetry add package-name`: add a dependency to the configuration file. You may have to `pip install package-name` as well so that you can do the test locally.


### Package management by Azure Artifacts.
- Set Up Azure Artifacts

  In Azure DevOps:
  Create a new feed in Azure Artifacts to host your Python package.
  Configure the feed's permissions as needed for your use case.
  Get the feed URL, which you will need to configure Poetry to publish the package.

- Configure Poetry for Azure Artifacts.
  
  The first line is to indicate the upload URL. You need to provide your own URL. The second line is to provide your username and personal access token.
```
poetry config repositories.azure [Feed URL]
poetry config http-basic.azure [Username] [PAT]
```

- Publish the package
  `poetry publish --repository azure`
