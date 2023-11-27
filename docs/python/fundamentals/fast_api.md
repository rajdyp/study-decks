![image](https://github.com/rajdyp/study-decks/assets/15313631/b8f909df-abaf-4e69-b8c2-d5f44b3e2ae7)

## Python type hints
- The `typing` module in Python provides support for type hints.
- Type hints are a way to indicate the expected types of values in function signatures, variables, and other places where types are relevant.

``` py
@api.get('/api/add')
def calculate(x: int, y: int):
    value = x + y
    return {
        'x': x,
        'y': y,
        'value': value
    }
```


## Pydantic model example (a.k.a BaseModel)

``` py
# API config
@api_router.get("/", response_model=schemas.Msg, status_code=200)
def root() -> dict:
    return {"msg": "This is the Example API"}

# schema
from pydantic import BaseModel

class Msg(BaseModel):
    msg: str
```
> `def root()` : This function is called path operator function i.e. function that is associated with a specific path and HTTP method.


## Pydantic classes for defining app config (a.k.a BaseSettings)

``` py
class LoggingSettings(BaseSettings):
    # logging levels are ints
    LOGGING_LEVEL: int = logging.INFO    # (1)!

class DBSettings(BaseSettings):
    SQLALCHEMY_DATABASE_URI: str

class Settings(BaseSettings):
    # 60 minutes * 24 hours * 8 = 8 days
    ACCESS_TOKEN_EXPIRE_MINUTES: int = 60 * 24 * 8

    logging: LoggingSettings = LoggingSettings()
    db: SQLLiteSettings = DBSettings()
```

1. `LOGGING_LEVEL: int = logging.INFO` : This is an argument with a default parameter.

## Dependency injection (a.k.a. handle code requirements)

``` py
# inject database dependency

from fastapi import Depends

# dependency function
def get_db() -> t.Generator:
    # SQLAlchemy ORM session
    db = SessionLocal()
    try:
        yield db
    finally:
        db.close()

# API config
@api_router.post("/signup", response_model=schemas.User, status_code=201)
def create_user_signup(
    # "Depends" specify database dependency
    *, db: Session = Depends(deps.get_db), user_in: schemas.CreateUser,
    ) -> Any:
    """
    Create new user without the need to be logged in.
    """
    user = db.query(User).filter(User.email == user_in.email).first()
    ...
```

!!! note

    asterisk (*) : Keyword-only arguments marker enforces use of keyword arguments to call the function, making the code 
    more readable and less error-prone, especially when dealing with functions that have multiple parameters.
 
    Call function with keyword arguments: `example = create_user_signup(db=db_session, user_in=user_data)`


## In-process background tasks

``` py
@router.post("/send-password-reset", status_code=200)
def send_password_reset(
    background_tasks: BackgroundTasks,
    user_in: schemas.UserPasswordResetEmail,
    ) -> Any:
    # Trigger email (asynchronous)
    background_tasks.add_task(
        send_password_reset_email,
        user=user_in,
    )
```


## SQLAlchemy

``` py
import typing as t
from sqlalchemy.ext.declarative import as_declarative, declared_attr

class_registry: t.Dict = {}

@as_declarative(class_registry=class_registry)
class Base:
    id: t.Any
    __name__: str

    # Generate __tablename__ automatically
    @declared_attr
    def __tablename__(cls) -> str:
        return cls.__name__.lower()
```

TL;DR: Applying @as_declarative to the Base class sets the stage for creating declarative base classes, and SQLAlchemy uses the class_registry to keep track of these classes for various ORM operations.

### @as_declarative on Base class
Applying @as_declarative to the Base class means that any class inheriting from Base will become a declarative base class.

### Inheritance and Class Registry
When we create a class that inherits from Base, it inherits the characteristics needed for SQLAlchemy to understand it as a declarative base class. The class_registry dictionary is used by SQLAlchemy to keep track of these classes.

### Automatic Table Naming
The __tablename__ method (decorated with @declared_attr) is a special method that SQLAlchemy recognizes. It automatically generates the name of the database table associated with the class. In this case, it's using the lowercase name of the class.

### Using Declarative Base Classes
Once we have declarative base classes, we can use them to define and interact with database tables. SQLAlchemy provides an ORM (Object-Relational Mapping) system that allows us to work with database records as if they were Python objects.
