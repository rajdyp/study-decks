``` py
from fastapi import FastAPI, APIRouter


app = FastAPI(title="Recipe API", openapi_url="/openapi.json")  # (1)

api_router = APIRouter()


@api_router.get("/", status_code=200)
def root() -> dict:
    """
    Root GET
    """
    return {"msg": "Hello, World!"}


app.include_router(api_router)


if __name__ == "__main__":
    # Use this for debugging purposes only
    import uvicorn

    uvicorn.run(app, host="0.0.0.0", port=8001, log_level="debug")
```

1.  FastAPI will automatically generate and expose the OpenAPI documentation for our API at the specified path (`/openapi.json`).


??? note annotate 

    Title: FastAPI Recipe API
    
    Summary:
    The provided code defines a simple FastAPI application with a single endpoint that returns a "Hello, World!" message. It also includes a router to organize API routes.
    
    1. Imports:
        - Imports FastAPI and (1) APIRouter from the FastAPI framework.
    
    2. App Initialization:
        - Creates a FastAPI app instance named app.
        - Sets the app's title as "Recipe API" and specifies the OpenAPI documentation URL.
    
    3. API Router Initialization:
        - Creates an API router instance named api_router using APIRouter().
    
    3. Root Endpoint:
        - Defines a root endpoint using the @api_router.get decorator.
        - The endpoint returns a dictionary with a "msg" key and the value "Hello, World!".
        - Specifies a 200 status code for a successful response.
    
    4. Include Router in App:
        - Includes the api_router in the main app using the app.include_router(api_router) statement.
    
    5. Debugging Configuration:
        - Checks if the script is being run as the main module (__name__ == "__main__").
        - If true, runs the FastAPI app using the uvicorn server for debugging purposes.
        - Configures uvicorn to run on host "0.0.0.0" and port 8001, with a log level of "debug".
    
    Usage:
    The FastAPI app serves a single endpoint ("/") that responds with a "Hello, World!" message.
    The app can be run locally for debugging using the provided if __name__ == "__main__" block.
    
    Note:
    The provided code is a basic example and can be extended to include more complex API routes and functionality.

1.  `APIRouter` is used to modularize and organize routes in a FastAPI application, providing better code structure, maintainability, and reusability as the application grows in complexity.
