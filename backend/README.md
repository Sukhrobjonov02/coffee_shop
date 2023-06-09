# Coffee Shop API Backend

Udacity has decided to open a new digitally enabled cafe for students to order drinks, socialize, and study hard. But they need help setting up their menu experience.

This application can:

1. Display graphics representing the ratios of ingredients in each drink.
2. Allow public users to view drink names and graphics.
3. Allow the shop baristas to see the recipe information.
4. Allow the shop managers to create new drinks and edit existing drinks.

The code follows [PEP 8 style guide](https://pep8.org/).

## Getting Started

### Installing Dependencies

#### Python 3.7

Follow instructions to install the latest version of python for your platform in the [python docs](https://docs.python.org/3/using/unix.html#getting-and-installing-the-latest-version-of-python)

#### Virtual Environment

We recommend working within a virtual environment whenever using Python for projects. This keeps your dependencies for each project separate and organized. Instructions for setting up a virtual environment for your platform can be found in the [python docs](https://packaging.python.org/guides/installing-using-pip-and-virtual-environments/)

#### PIP Dependencies

Once you have your virtual environment setup and running, install dependencies by naviging to the `/backend` directory and running:

```bash
pip install -r requirements.txt
```

This will install all of the required packages we selected within the `requirements.txt` file.

##### Key Dependencies

- [Flask](http://flask.pocoo.org/) is a lightweight backend microservices framework. Flask is required to handle requests and responses.

- [SQLAlchemy](https://www.sqlalchemy.org/) and [Flask-SQLAlchemy](https://flask-sqlalchemy.palletsprojects.com/en/2.x/) are libraries to handle the lightweight sqlite database. Since we want you to focus on auth, we handle the heavy lift for you in `./src/database/models.py`. We recommend skimming this code first so you know how to interface with the Drink model.

- [jose](https://python-jose.readthedocs.io/en/latest/) JavaScript Object Signing and Encryption for JWTs. Useful for encoding, decoding, and verifying JWTS.

## Running the server

From within the `./src` directory first ensure you are working using your created virtual environment.

Each time you open a new terminal session, run:

```bash
export FLASK_APP=api.py
export FLASK_ENV=development
```

To run the server, execute:

```bash
flask run --reload
```

The `--reload` flag will detect file changes and restart the server automatically.

### API Testing

If you want to test the API, you can import `udacity-fsnd-udaspicelatte.postman_collection.json` file to [Postman](https://www.postman.com/downloads/) and run all tests using the [Collection Runner](https://learning.postman.com/docs/postman/collection-runs/starting-a-collection-run/).

## API Reference

### Getting Started
- Base URL: At present this app can only be run locally and is not hosted as a base URL. The backend app is hosted at the default, `http://127.0.0.1:5000/`, which is set as a proxy in the frontend configuration.

### Authentication

The Coffee Shop API uses JSON Web Token (JWT) to authenticate requests.

Users have to authenticate via bearer auth by using `-H "Authorization: Bearer token`.

### Error Handling
Errors are returned as JSON objects in the following format:
```
{
    "success": False, 
    "error": 400,
    "message": "bad request"
}
```
The API will return three error types when requests fail:
- 400: Bad Request
- 404: Resource Not Found
- AuthError: Authentication Error

### Endpoints
#### GET /questions
- General:
    - Returns a list of Drink with a short form of the recipe.
- Sample: `curl http://127.0.0.1:5000/drinks`

```
{
    "drinks": [
        {
            "id": 1,
            "recipe": [
                {
                    "color": "blue",
                    "parts": 1
                }
            ],
            "title": "water"
        }
    ],
    "succes": true
}
```

#### GET /drinks-detail
- General:
    - Returns a list of Drink with a long form of the recipe.
- Sample: `curl http://127.0.0.1:5000/drinks-detail`

```
{
    "drinks": [
        {
            "id": 1,
            "recipe": [
                {
                    "color": "blue",
                    "name": "water",
                    "parts": 1
                }
            ],
            "title": "water"
        }
    ],
    "success": true
}
```

#### POST /drinks
- General:
    - Adds a new drink using the submitted title and recipe properties (both of them are required).
- Sample: `curl http://127.0.0.1:5000/drinks -X POST -H "Content-Type: application/json" -d '{"recipe":{"color":"milky","name":"coffee with milk","parts":1},"title":"Coffee Milk"}'`

```
{
  "drinks": [
    {
      "id": 10,
      "recipe": [
        {
          "color": "milky",
          "name":"coffee with milk",
          "parts": 1
        }
      ],
      "title": "Coffee Milk"
    }
  ],
  "success": true
}
```

#### PATCH /drinks/{drink_id}
- General:
    - Updates an existing drink using the submitted title and/or recipe properties. Can update both title and recipe or only one that was provided.
- Sample: `curl http://127.0.0.1:5000/drinks/15 -X PATCH -H "Content-Type: application/json" -d '{"title": "Cappuccino"}'`

```
{
  "drinks": [
    {
      "id": 15
      "recipe": [
        {
          "color": "milky",
          "parts": 1
        }
      ],
      "title": "Cappuccino"
    }
  ],
  "success": true
}
```

#### DELETE /drinks/{drink_id}
- General:
    - Deletes an existing drink (if it exists) by given `ID`.
- Sample: `curl http://127.0.0.1:5000/drinks/15 -X DELETE`

```
{
  "delete": 20,
  "success": true
}
```

## Deployment N/A

## Authors
Abdulaziz Sukhrobjonov - [LinkedIn](https://www.linkedin.com/in/abdulaziz-sukhrobjonov/) | [GitHub](https://github.com/Sukhrobjonov02)

## Acknowledgments
Diyorbek Azimqulov - My groupmate from university [LinkedIn](https://www.linkedin.com/in/diyorbek-azimqulov-40675a1b9/) | [GitHub](https://github.com/DiyorbekAzimqulov)

## License

`The Treasure Library` is a public domain work, dedicated using
[CC0 1.0](https://creativecommons.org/publicdomain/zero/1.0/). Feel free to do
whatever you want with it.