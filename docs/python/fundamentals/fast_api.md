![image](https://github.com/rajdyp/study-decks/assets/15313631/b8f909df-abaf-4e69-b8c2-d5f44b3e2ae7)

## Python type hints

```{ .python .copy .select}
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

```python
# API config
@api_router.get("/", response_model=schemas.Msg, status_code=200)
def root() -> dict:
    return {"msg": "This is the Example API"}

# schema
from pydantic import BaseModel

class Msg(BaseModel):
    msg: str
```


## Pydantic classes for defining app config (a.k.a BaseSettings)

```python
class LoggingSettings(BaseSettings):
    # logging levels are ints
    LOGGING_LEVEL: int = logging.INFO    # (1)

class DBSettings(BaseSettings):
    SQLALCHEMY_DATABASE_URI: str

class Settings(BaseSettings):
    # 60 minutes * 24 hours * 8 = 8 days
    ACCESS_TOKEN_EXPIRE_MINUTES: int = 60 * 24 * 8

    logging: LoggingSettings = LoggingSettings()
    db: SQLLiteSettings = DBSettings()
```

1.  :man_raising_hand: LOGGING_LEVEL: int = logging.INFO -> argument with a default parameter


## Dependency injection (a.k.a. handle code requirements)

```python
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

<div class="result" markdown>

!!! note

    * : Keyword-only arguments marker
        Enforces use of keyword arguments to call the function, making the code more readable and less error-prone, 
        especially when dealing with functions that have multiple parameters

    # call function with keyword arguments
    example = create_user_signup(db=db_session, user_in=user_data)
</div>


## In-process background tasks

```python
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
