# Initial Setup (for project creation)
## Install Poetry
```
curl -sSL https://install.python-poetry.org | python3 - --uninstall
curl -sSL https://install.python-poetry.org | python3 -
```
## Configure Poetry
```
poetry config virtualenvs.in-project true
poetry config --list
```
## Create a Poetry project
```
poetry new <folder name, eg. backend>
cd <folder name, eg. backend>
```
## Update Poetry metadata
```
[tool.poetry]
name = "<project name, eg. courselens-backend>"
version = "<version number, eg. 1.0.0>"
description = "<description, eg. CourseLens Backend>"
authors = ["<author info, eg. Wang Shining <e0253746@u.nus.edu>>"]
package-mode = false

[tool.poetry.dependencies]
python = "^3.9"
```
## Add FastAPI Server dependencies
```
poetry add fastapi uvicorn sqlmodel pydantic pydantic_settings apscheduler psycopg2-binary@2.9.9
```
## Update directory structure
- clear content under src folder
- cd src
- create empty \_\_init\_\_.py to mark src as a python package
- create empty main.py as the application's main entry point
- create settings.py to control application configurations (need dependency pydantic and pydantic_settings)
```
from pydantic import Field
from pydantic_settings import BaseSettings
import logging


logging.basicConfig(level=logging.INFO, format="%(asctime)s - %(name)s - %(levelname)s - %(message)s")
logging.getLogger("src").setLevel(logging.DEBUG)
log = logging.getLogger(__name__)

class Settings(BaseSettings):
	app_name: str = Field("default", env="APP_NAME")
	debug: bool = Field(False, env="DEBUG")
	...

settings = Settings()

log.info("===================Application Settings===================")
_config = settings.model_dump()
_max_len = max([len(k) for k in _config.keys()])
for k, v in settings.model_dump().items():
	log.info(f"{k:{_max_len}} = {v}")
```

# Developer Setup
## Install Poetry
```
curl -sSL https://install.python-poetry.org | python3 - --uninstall
curl -sSL https://install.python-poetry.org | python3 -
```
## Configure Poetry
```
poetry config virtualenvs.in-project true
poetry config --list
```
## Pull source code from Github
Use `git pull ...` or any git management tools like sourcetree
## Configure Poetry environment
```
cd <poetry project folder name, eg. ./backend>
poetry env use <path to Python, eg. /opt/homebrew/bin/python3.9>
```
## Poetry install existing dependencies
```
poetry install
```
## Configure IDE Python interpreter path to use poetry env
```
/Users/shining/personal/NUS/CS5224_Cloud_Computing/courselens/backend/.venv/bin/python3.9
```
## Add lib
```
poetry add fastapi
poetry add uvicorn
poetry add sqlmodel
```
## Remove lib
```
poetry remove sqlmodel
poetry remove pydantic
```
## Run FastAPI server
```
poetry run uvicorn src.main:app --reload
```
