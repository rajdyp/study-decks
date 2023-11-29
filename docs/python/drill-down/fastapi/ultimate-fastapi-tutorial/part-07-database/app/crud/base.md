``` py
from typing import Any, Dict, Generic, List, Optional, Type, TypeVar, Union

from fastapi.encoders import jsonable_encoder
from pydantic import BaseModel
from sqlalchemy.orm import Session

from app.db.base_class import Base

ModelType = TypeVar("ModelType", bound=Base)
CreateSchemaType = TypeVar("CreateSchemaType", bound=BaseModel)
UpdateSchemaType = TypeVar("UpdateSchemaType", bound=BaseModel)


class CRUDBase(Generic[ModelType, CreateSchemaType, UpdateSchemaType]):
    def __init__(self, model: Type[ModelType]):
        """
        CRUD object with default methods to Create, Read, Update, Delete (CRUD).
        **Parameters**
        * `model`: A SQLAlchemy model class
        * `schema`: A Pydantic model (schema) class
        """
        self.model = model

    def get(self, db: Session, id: Any) -> Optional[ModelType]:
        return db.query(self.model).filter(self.model.id == id).first()

    def get_multi(
        self, db: Session, *, skip: int = 0, limit: int = 100
    ) -> List[ModelType]:
        return db.query(self.model).offset(skip).limit(limit).all()

    def create(self, db: Session, *, obj_in: CreateSchemaType) -> ModelType:
        obj_in_data = jsonable_encoder(obj_in)
        db_obj = self.model(**obj_in_data)  # type: ignore
        db.add(db_obj)
        db.commit()
        db.refresh(db_obj)
        return db_obj

    def update(
        self,
        db: Session,
        *,
        db_obj: ModelType,
        obj_in: Union[UpdateSchemaType, Dict[str, Any]]
    ) -> ModelType:
        obj_data = jsonable_encoder(db_obj)
        if isinstance(obj_in, dict):
            update_data = obj_in
        else:
            update_data = obj_in.dict(exclude_unset=True)
        for field in obj_data:
            if field in update_data:
                setattr(db_obj, field, update_data[field])
        db.add(db_obj)
        db.commit()
        db.refresh(db_obj)
        return db_obj

    def remove(self, db: Session, *, id: int) -> ModelType:
        obj = db.query(self.model).get(id)
        db.delete(obj)
        db.commit()
        return obj
```

??? note

    Title: CRUD Base Implementation with Type Hints
    
    Summary:
    The provided code defines a generic CRUD (Create, Read, Update, Delete) base class, `CRUDBase`, using type hints for flexibility and 
    clarity. It is designed to work with SQLAlchemy (1) models and Pydantic schemas.
    { .annotate }
    1.  test
    
    1. Imports:
        - The code imports various types and modules, including `Any`, `Dict`, `Generic` (1) , `List`, `Optional`, `Type`, `TypeVar` (2) , and `Union`.
        { .annotate }
    
        1.  `Generic` is a feature from the typing module. 
            It allows us to create generic classes or functions that can work with different types while preserving type hints. 
            By using Generic, we can define classes or functions with type parameters that are only resolved when an instance or function call is made. 
            It is particularly useful for creating reusable and type-safe code that can operate on a variety of types.
        
        2.  `TypeVar` is a generic type variable introduced in Python's typing module.
            It is used to declare a placeholder for a type that will be specified later.
            It allows us to create functions or classes that can work with different types without specifying the exact type until it is used.
            `TypeVar` can have an optional bound parameter, which restricts the type to a particular base class or type.
        - It uses `jsonable_encoder` from  `fastapi.encoders`, `BaseModel` from `pydantic`, and `Session` from `sqlalchemy.orm`.
        - `ModelType`, `CreateSchemaType`, and `UpdateSchemaType` are defined as type variables (`TypeVar`) for flexibility in generic class 
        definition.
        
    2. Type Variables:
        - `ModelType`: Represents the SQLAlchemy model type bound to the `Base` class.
        - `CreateSchemaType`: Represents the type of Pydantic schema used for creating objects.
        - `UpdateSchemaType`: Represents the type of Pydantic schema used for updating objects.
    
    3. CRUDBase Class:
        - Initialization:
          - Takes a `model` parameter, which is a SQLAlchemy model class.
        - Methods:
          - `get`: Retrieves a single object by ID from the database.
          - `get_multi`: Retrieves a list of objects with optional pagination parameters.
          - `create`: Creates a new object in the database using a Pydantic schema.
          - `update`: Updates an object in the database using a Pydantic schema or a dictionary.
          - `remove`: Deletes an object from the database by ID.
      
    4. Method Details:
        - `get`: Queries the database using the model's ID field.
        - `get_multi`: Queries the database with optional skip and limit parameters.
        - `create`: Converts the Pydantic schema into JSON, creates a new object, and commits it to the database.
        - `update`: Converts the object and input data into JSON, updates the object's fields, and commits changes.
        - `remove`: Deletes an object from the database.
    
    Usage:
    This generic `CRUDBase` class can be used as a base class for specific CRUD implementations for different SQLAlchemy models and Pydantic 
    schemas. It provides reusable and type-safe methods for common database operations.
    
    Lorem ipsum dolor sit amet, (1) consectetur adipiscing elit.
    { .annotate }
    
    1.  :man_raising_hand: I'm an annotation! I can contain `code`, __formatted
        text__, images, ... basically anything that can be expressed in Markdown.
