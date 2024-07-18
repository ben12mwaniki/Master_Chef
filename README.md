# Master Chef
## Introduction
A website forum to share recipes and other cooking related tips. This project was originally meant to fulfill requirements for a course _ECSE 428 - Software Engineering Practice_ at McGill University in Fall 2022.

## Contributors
Contributors: Ruoli Wang, Sia Ham, Tyler Syme, Zheyan Tu, Sandy Lao, Theodore Peters, Paul Teng, Niilo Vuokila, Jasmine Cheung and myself (Ben Mwaniki). 

## Setting up the environment

### Prerequisites

*  Python 3
*  Postgres 16

### Steps

1.  Clone the repo and navigate into the repo directory
2.  Create a Python virtual environment (***optional, but good idea***)

```sh
python -m venv .venv
```

3.  Activate the .venv

```sh
source .venv/bin/activate    # for linux or mac
.venv\Scripts\activate.bat   # for cmd.exe
.venv\Scripts\activate       # for powershell
```

4.  Install the dependencies

```sh
pip install -r requirements.txt
```

At this point, you are ready to [run the app](#running-the-app) or [run the tests](#running-the-tests).

As a side note,
to exit / deactivate the venv, do

```sh
deactivate
```

## Running the app

Once the environment is setup, you can start the app:

```sh
flask run
```

### Configuration

Parts of the app's behavior must / can be configured via environment variables

| Environment Variable | Values | Default Value | Purpose |
|----------------------|--------|-----------|---------|
| `DEBUG` | boolean | `false` | Run in debug mode when true (which, among other things, means the app will automatically load changes to the code without needing to be rerun) |
| `POSTGRES_USER` | db login username | `postgres` | The app uses this to login to the postgres server |
| `POSTGRES_PASSWORD` | db login password | ***Mandatory*** | The app uses this to login to the postgres server |
| `POSTGRES_DB` | db name | follows variable `POSTGRES_USER` | The database name in which the tables exist / will be created under |
| `POSTGRES_HOST` | hostname or IP | `localhost` | The address of the postgres server |
| `POSTGRES_PORT` | port number | `5432` | The port of the postgres server |

## Running the tests

Once the environment is setup, you can also run the tests:

```sh
pytest --cov=project --cov-branch --cov-report term
```

***Note: For Windows folks***

Due to unfortunate database stuff, you also need to supply a running database when testing
(just like how you would if you run the app).
***Warning: Whatever you pick, it likely will destroy existing data, so don't supply the production database!!!***
