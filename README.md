# pof_fast_api

Proof of concept of pyhton fast api: <https://fastapi.tiangolo.com/>

## Installation

    pip install fastapi
    pip install uvicorn
Yoy can recevie this warning: The script uvicorn is installed in '$HOME/.local/bin' which is not on PATH. You need add it to the path to run the next command
    uvicorn main:app --reload

To see the API documentation with swagger: <http://127.0.0.1:8000/docs>  
To see the APU documentation with redoc: <http://127.0.0.1:8000/redoc>

## Poetry

<https://python-poetry.org/>

```shell
poetry init
```

```shell
poetry install
```

## To build this project with Docker

Build images with:

```shell
docker build --tag poetry-project --file docker/Dockerfile .
```

The Dockerfile uses multi-stage builds to run lint and test stages before building the production stage.
If linting or testing fails the build will fail.

You can stop the build at specific stages with the `--target` option:

```shell
docker build --name poetry-project --file docker/Dockerfile . --target <stage>
```

For example we wanted to stop at the **test** stage:

```shell
docker build --tag poetry-project --file docker/Dockerfile --target test .
```

We could then get a shell inside the container with:

```shell
docker run -it poetry-project:latest bash
```

If you do not specify a target the resulting image will be the last image defined which in our case is the 'production' image.

To run the project in your local machine:

```shell
docker run --rm -it -p 127.0.0.1:8000:8000 poetry-project
```

( The project was dockerized using this exapmle: <https://github.com/svx/poetry-fastapi-docker> )


## Next steps

* Work with gino <https://python-gino.org/docs/en/1.1b2/tutorials/fastapi.html>
