# FastAPI Python Backend Memory

## Project Overview

This is a **FastAPI backend API** built with Python 3.10+. We follow modern async patterns, type hints everywhere, and API-first design principles.

## Tech Stack

### Core Framework
- **FastAPI 0.104+** (Async web framework)
- **Python 3.10+** (Type hints, async/await)
- **Pydantic V2** (Data validation)
- **Uvicorn** (ASGI server)

### Database
- **SQLAlchemy 2.0** (Async ORM)
- **Alembic** (Database migrations)
- **PostgreSQL** (Primary database)
- **Redis** (Caching, sessions)

### Authentication
- **JWT** (JSON Web Tokens)
- **OAuth2** with Password (and Bearer) flow
- **BCrypt** for password hashing

### Testing
- **Pytest** (Test framework)
- **Pytest-Async** (Async tests)
- **HTTPX** (HTTP client for testing)

### Additional Tools
- **Pydantic Settings** (Configuration)
- **Python-Multipart** (File uploads)
- **Python-JOSE** (JWT handling)

## Project Structure

```
/app
  /api                 - API endpoints
    /v1                - API version 1
      /endpoints       - Route handlers
        users.py
        auth.py
        items.py
      __init__.py      - API router
  /core                - Core functionality
    config.py          - Configuration
    security.py        - Auth/security utilities
    deps.py            - Dependencies
  /db                  - Database
    /models            - SQLAlchemy models
    /schemas           - Pydantic schemas
    session.py         - Database session
    base.py            - Base model
  /services            - Business logic
    user_service.py
    auth_service.py
  /utils               - Utilities
    logging.py
    email.py
  main.py              - FastAPI application

/tests                 - Test files
  /api                 - API tests
  /services            - Service tests
  conftest.py          - Pytest fixtures

/alembic               - Database migrations
  /versions            - Migration files
  env.py               - Alembic config

.env                   - Environment variables (gitignored)
.env.example           - Environment template
requirements.txt       - Dependencies
pyproject.toml         - Python project config
```

## File Naming Conventions

- **snake_case** for all Python files: `user_service.py`
- **PascalCase** for classes: `UserService`, `UserModel`
- **snake_case** for functions: `get_current_user()`, `create_access_token()`
- **UPPER_SNAKE_CASE** for constants: `ACCESS_TOKEN_EXPIRE_MINUTES`

## Coding Conventions

### Type Hints (Always)

```python
from typing import Optional, List
from datetime import datetime

def get_user(user_id: int) -> Optional[User]:
    """Get user by ID."""
    pass

async def get_users(
    skip: int = 0,
    limit: int = 100
) -> List[User]:
    """Get list of users."""
    pass
```

### Pydantic Schemas

**Define request/response models:**
```python
from pydantic import BaseModel, EmailStr, Field

class UserBase(BaseModel):
    email: EmailStr
    username: str = Field(..., min_length=3, max_length=50)
    full_name: Optional[str] = None

class UserCreate(UserBase):
    password: str = Field(..., min_length=8)

class UserResponse(UserBase):
    id: int
    is_active: bool
    created_at: datetime

    class Config:
        from_attributes = True
```

### API Endpoints

**Router structure:**
```python
from fastapi import APIRouter, Depends, HTTPException, status
from sqlalchemy.ext.asyncio import AsyncSession

from app.core.deps import get_db, get_current_user
from app.db.schemas import UserCreate, UserResponse
from app.services import user_service

router = APIRouter(prefix="/users", tags=["users"])

@router.post(
    "/",
    response_model=UserResponse,
    status_code=status.HTTP_201_CREATED,
    summary="Create new user"
)
async def create_user(
    user_in: UserCreate,
    db: AsyncSession = Depends(get_db)
) -> UserResponse:
    """
    Create a new user with the following information:
    
    - **email**: User email address
    - **username**: Unique username
    - **password**: Strong password (min 8 characters)
    """
    user = await user_service.create_user(db, user_in)
    return user

@router.get(
    "/{user_id}",
    response_model=UserResponse,
    summary="Get user by ID"
)
async def get_user(
    user_id: int,
    db: AsyncSession = Depends(get_db),
    current_user = Depends(get_current_user)
) -> UserResponse:
    """Get user details by ID."""
    user = await user_service.get_user(db, user_id)
    if not user:
        raise HTTPException(
            status_code=status.HTTP_404_NOT_FOUND,
            detail="User not found"
        )
    return user
```

### SQLAlchemy Models (Async)

```python
from sqlalchemy import Column, Integer, String, Boolean, DateTime
from sqlalchemy.sql import func
from app.db.base import Base

class User(Base):
    __tablename__ = "users"

    id = Column(Integer, primary_key=True, index=True)
    email = Column(String, unique=True, index=True, nullable=False)
    username = Column(String, unique=True, index=True, nullable=False)
    hashed_password = Column(String, nullable=False)
    full_name = Column(String, nullable=True)
    is_active = Column(Boolean, default=True)
    created_at = Column(DateTime(timezone=True), server_default=func.now())
    updated_at = Column(DateTime(timezone=True), onupdate=func.now())
```

### Database Sessions (Async)

```python
from sqlalchemy.ext.asyncio import create_async_engine, AsyncSession
from sqlalchemy.orm import sessionmaker

engine = create_async_engine(DATABASE_URL, echo=True)
async_session = sessionmaker(
    engine, class_=AsyncSession, expire_on_commit=False
)

async def get_db() -> AsyncSession:
    async with async_session() as session:
        try:
            yield session
        finally:
            await session.close()
```

### Service Layer

**Business logic in services:**
```python
from sqlalchemy.ext.asyncio import AsyncSession
from sqlalchemy import select
from typing import Optional, List

from app.db.models import User
from app.db.schemas import UserCreate
from app.core.security import get_password_hash

class UserService:
    @staticmethod
    async def create_user(db: AsyncSession, user_in: UserCreate) -> User:
        """Create a new user."""
        user = User(
            email=user_in.email,
            username=user_in.username,
            hashed_password=get_password_hash(user_in.password),
            full_name=user_in.full_name
        )
        db.add(user)
        await db.commit()
        await db.refresh(user)
        return user

    @staticmethod
    async def get_user(db: AsyncSession, user_id: int) -> Optional[User]:
        """Get user by ID."""
        result = await db.execute(
            select(User).where(User.id == user_id)
        )
        return result.scalar_one_or_none()

    @staticmethod
    async def get_users(
        db: AsyncSession,
        skip: int = 0,
        limit: int = 100
    ) -> List[User]:
        """Get list of users."""
        result = await db.execute(
            select(User).offset(skip).limit(limit)
        )
        return result.scalars().all()

user_service = UserService()
```

### Authentication

**JWT tokens:**
```python
from datetime import datetime, timedelta
from jose import jwt
from passlib.context import CryptContext

pwd_context = CryptContext(schemes=["bcrypt"], deprecated="auto")

def verify_password(plain_password: str, hashed_password: str) -> bool:
    """Verify a password against a hash."""
    return pwd_context.verify(plain_password, hashed_password)

def get_password_hash(password: str) -> str:
    """Hash a password."""
    return pwd_context.hash(password)

def create_access_token(data: dict, expires_delta: timedelta = None) -> str:
    """Create a JWT access token."""
    to_encode = data.copy()
    expire = datetime.utcnow() + (expires_delta or timedelta(minutes=15))
    to_encode.update({"exp": expire})
    return jwt.encode(to_encode, SECRET_KEY, algorithm=ALGORITHM)
```

**Dependencies:**
```python
from fastapi import Depends, HTTPException, status
from fastapi.security import OAuth2PasswordBearer
from jose import JWTError, jwt

oauth2_scheme = OAuth2PasswordBearer(tokenUrl="api/v1/auth/login")

async def get_current_user(
    token: str = Depends(oauth2_scheme),
    db: AsyncSession = Depends(get_db)
) -> User:
    """Get current authenticated user."""
    credentials_exception = HTTPException(
        status_code=status.HTTP_401_UNAUTHORIZED,
        detail="Could not validate credentials",
        headers={"WWW-Authenticate": "Bearer"},
    )
    try:
        payload = jwt.decode(token, SECRET_KEY, algorithms=[ALGORITHM])
        user_id: int = payload.get("sub")
        if user_id is None:
            raise credentials_exception
    except JWTError:
        raise credentials_exception
    
    user = await user_service.get_user(db, user_id=user_id)
    if user is None:
        raise credentials_exception
    return user
```

## Error Handling

**Consistent error responses:**
```python
from fastapi import HTTPException, status

# Not Found
raise HTTPException(
    status_code=status.HTTP_404_NOT_FOUND,
    detail="Resource not found"
)

# Validation Error
raise HTTPException(
    status_code=status.HTTP_400_BAD_REQUEST,
    detail="Invalid input data"
)

# Unauthorized
raise HTTPException(
    status_code=status.HTTP_401_UNAUTHORIZED,
    detail="Not authenticated",
    headers={"WWW-Authenticate": "Bearer"}
)

# Forbidden
raise HTTPException(
    status_code=status.HTTP_403_FORBIDDEN,
    detail="Not enough permissions"
)
```

## Configuration

**Pydantic Settings:**
```python
from pydantic_settings import BaseSettings

class Settings(BaseSettings):
    PROJECT_NAME: str = "FastAPI Project"
    VERSION: str = "1.0.0"
    API_V1_STR: str = "/api/v1"
    
    DATABASE_URL: str
    SECRET_KEY: str
    ALGORITHM: str = "HS256"
    ACCESS_TOKEN_EXPIRE_MINUTES: int = 30
    
    # CORS
    BACKEND_CORS_ORIGINS: list[str] = []
    
    # Redis
    REDIS_URL: str = "redis://localhost:6379"
    
    class Config:
        env_file = ".env"
        case_sensitive = True

settings = Settings()
```

## CORS Configuration

```python
from fastapi.middleware.cors import CORSMiddleware

app.add_middleware(
    CORSMiddleware,
    allow_origins=settings.BACKEND_CORS_ORIGINS,
    allow_credentials=True,
    allow_methods=["*"],
    allow_headers=["*"],
)
```

## Database Migrations

**Create migration:**
```bash
alembic revision --autogenerate -m "Add users table"
```

**Run migrations:**
```bash
alembic upgrade head
```

**Downgrade:**
```bash
alembic downgrade -1
```

## Testing Patterns

**Fixtures:**
```python
import pytest
from httpx import AsyncClient
from sqlalchemy.ext.asyncio import AsyncSession

@pytest.fixture
async def client() -> AsyncClient:
    async with AsyncClient(app=app, base_url="http://test") as client:
        yield client

@pytest.fixture
async def test_user(db: AsyncSession) -> User:
    user = await user_service.create_user(
        db,
        UserCreate(
            email="test@example.com",
            username="testuser",
            password="testpass123"
        )
    )
    return user
```

**Test examples:**
```python
@pytest.mark.asyncio
async def test_create_user(client: AsyncClient):
    response = await client.post(
        "/api/v1/users/",
        json={
            "email": "newuser@example.com",
            "username": "newuser",
            "password": "password123"
        }
    )
    assert response.status_code == 201
    data = response.json()
    assert data["email"] == "newuser@example.com"
    assert "id" in data

@pytest.mark.asyncio
async def test_get_user(client: AsyncClient, test_user: User):
    response = await client.get(f"/api/v1/users/{test_user.id}")
    assert response.status_code == 200
    data = response.json()
    assert data["id"] == test_user.id
```

## API Documentation

FastAPI auto-generates docs at:
- **Swagger UI:** `/docs`
- **ReDoc:** `/redoc`

**Enhance with:**
```python
app = FastAPI(
    title="My API",
    description="API description",
    version="1.0.0",
    docs_url="/docs",
    redoc_url="/redoc",
    openapi_url="/api/v1/openapi.json"
)
```

## Logging

```python
import logging

logging.basicConfig(
    level=logging.INFO,
    format="%(asctime)s - %(name)s - %(levelname)s - %(message)s"
)

logger = logging.getLogger(__name__)

# Usage
logger.info("User created", extra={"user_id": user.id})
logger.error("Failed to create user", exc_info=True)
```

## Performance Optimization

### Background Tasks
```python
from fastapi import BackgroundTasks

@router.post("/send-email/")
async def send_email(
    email: str,
    background_tasks: BackgroundTasks
):
    background_tasks.add_task(send_email_task, email)
    return {"message": "Email will be sent"}
```

### Caching
```python
from redis import asyncio as aioredis

redis = await aioredis.from_url(REDIS_URL)

async def get_cached_user(user_id: int):
    cached = await redis.get(f"user:{user_id}")
    if cached:
        return json.loads(cached)
    
    user = await user_service.get_user(db, user_id)
    await redis.setex(
        f"user:{user_id}",
        3600,  # 1 hour
        json.dumps(user.dict())
    )
    return user
```

## Commands

```bash
# Run development server
uvicorn app.main:app --reload

# Run with custom port
uvicorn app.main:app --reload --port 8080

# Run tests
pytest

# Run tests with coverage
pytest --cov=app --cov-report=html

# Create migration
alembic revision --autogenerate -m "description"

# Run migrations
alembic upgrade head

# Format code
black app/
isort app/

# Lint
flake8 app/
mypy app/
```

## Common Patterns to Follow

### 1. Always Use Type Hints
Every function, method, and variable should have type hints

### 2. Use Async/Await
All database operations and I/O should be async

### 3. Service Layer Pattern
Business logic in services, not in route handlers

### 4. Pydantic for Validation
Use Pydantic models for all request/response data

### 5. Dependency Injection
Use FastAPI's dependency system for database sessions, current user, etc.

### 6. Proper HTTP Status Codes
Use appropriate status codes (201 for created, 404 for not found, etc.)

### 7. API Versioning
Version your API (/api/v1/, /api/v2/)

### 8. Comprehensive Docstrings
Document all endpoints, functions, and classes

## Important Notes

- **Async everywhere** - Use `async def` for all route handlers
- **Pydantic V2** - We use the latest Pydantic version
- **SQLAlchemy 2.0** - Use the new async API
- **Type hints required** - No dynamic typing
- **Migrations** - Never modify database directly, always use Alembic
- **Dependencies** - Use FastAPI's dependency injection
- **Testing** - Write tests for all endpoints

## Links & Resources

- [FastAPI Documentation](https://fastapi.tiangolo.com/)
- [Pydantic Documentation](https://docs.pydantic.dev/)
- [SQLAlchemy Async](https://docs.sqlalchemy.org/en/20/orm/extensions/asyncio.html)
- [Alembic Documentation](https://alembic.sqlalchemy.org/)
