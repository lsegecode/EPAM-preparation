# Task Manager API - Learning Project Guide

## 🎯 Project Overview

A RESTful API to manage tasks (like a to-do list) built with **FastAPI** and **Python**. This project is designed to help you practice core Python concepts that commonly appear in technical interviews.

---

## 📁 Project Structure

```
task-manager-api/
│
├── venv/                    # Your virtual environment (already created!)
│
├── app/
│   ├── __init__.py          # Makes 'app' a Python package
│   ├── main.py              # FastAPI application entry point
│   ├── models.py            # Pydantic models (data validation)
│   ├── schemas.py           # Database schemas (SQLAlchemy)
│   ├── database.py          # Database connection setup
│   ├── crud.py              # Create, Read, Update, Delete operations
│   └── routers/
│       ├── __init__.py
│       └── tasks.py         # Task-related endpoints
│
├── tests/
│   ├── __init__.py
│   └── test_tasks.py        # Unit tests for task endpoints
│
├── requirements.txt         # Project dependencies
├── .gitignore               # Files to ignore in git
└── README.md                # Project documentation
```

---

## 🛠️ Functionalities & Interview Concepts

### Phase 1: Basic Setup
| What You'll Build | Python Concepts for Interview |
|-------------------|-------------------------------|
| Virtual environment | **Package management**, isolation of dependencies |
| `requirements.txt` | **pip**, dependency management |
| Basic FastAPI app | **Decorators** (`@app.get`), **functions** |

---

### Phase 2: Task Model (Pydantic)
| What You'll Build | Python Concepts for Interview |
|-------------------|-------------------------------|
| `Task` model | **Classes**, **OOP**, **Type Hints** |
| Field validation | **Data validation**, **Pydantic** |
| Optional fields | **Optional types**, **default values** |

**Example in Interview:**
> "How do you validate data in Python?"  
> You'll answer: "I can use Pydantic models with type hints for automatic validation..."

```python
from pydantic import BaseModel
from typing import Optional
from datetime import datetime

class Task(BaseModel):
    id: int
    title: str
    description: Optional[str] = None
    completed: bool = False
    created_at: datetime
```

---

### Phase 3: CRUD Operations
| What You'll Build | Python Concepts for Interview |
|-------------------|-------------------------------|
| Create task | **POST requests**, **dictionaries**, **list operations** |
| Read tasks | **GET requests**, **list comprehension**, **filtering** |
| Update task | **PUT/PATCH**, **dictionary updates** |
| Delete task | **DELETE**, **exception handling** |

**Example in Interview:**
> "How would you filter a list of objects?"  
> You'll answer: "Using list comprehension: `[task for task in tasks if task.completed]`"

---

### Phase 4: Database Integration
| What You'll Build | Python Concepts for Interview |
|-------------------|-------------------------------|
| SQLite database | **SQL basics**, **database connections** |
| SQLAlchemy models | **ORM**, **classes with inheritance** |
| Database sessions | **Context managers** (`with` statement) |
| Dependency injection | **Decorators**, **generators** (`yield`) |

**Example in Interview:**
> "Explain the `yield` keyword"  
> You'll answer: "It creates a generator. In FastAPI, I use it for dependency injection to manage database sessions..."

---

### Phase 5: Error Handling
| What You'll Build | Python Concepts for Interview |
|-------------------|-------------------------------|
| 404 Not Found | **HTTPException**, **custom exceptions** |
| Validation errors | **try/except blocks** |
| Custom error messages | **Exception classes** |

**Example in Interview:**
> "How do you handle errors in Python?"  
> You'll answer: "Using try/except blocks, and I can create custom exceptions..."

```python
from fastapi import HTTPException

def get_task(task_id: int):
    task = find_task_by_id(task_id)
    if not task:
        raise HTTPException(status_code=404, detail="Task not found")
    return task
```

---

### Phase 6: Async/Await
| What You'll Build | Python Concepts for Interview |
|-------------------|-------------------------------|
| Async endpoints | **async/await**, **coroutines** |
| Async database calls | **asynchronous programming** |

**Example in Interview:**
> "What is async/await in Python?"  
> You'll answer: "It allows non-blocking I/O operations. The function suspends while waiting and other code can run..."

```python
@app.get("/tasks")
async def get_all_tasks():
    tasks = await fetch_tasks_from_db()
    return tasks
```

---

### Phase 7: Testing
| What You'll Build | Python Concepts for Interview |
|-------------------|-------------------------------|
| Unit tests | **pytest**, **testing fundamentals** |
| Test client | **mocking**, **fixtures** |
| Test coverage | **test-driven development** |

---

## 🔗 API Endpoints We'll Build

| Method | Endpoint | Description |
|--------|----------|-------------|
| `GET` | `/tasks` | Get all tasks |
| `GET` | `/tasks/{id}` | Get a specific task |
| `POST` | `/tasks` | Create a new task |
| `PUT` | `/tasks/{id}` | Update a task |
| `DELETE` | `/tasks/{id}` | Delete a task |
| `GET` | `/tasks?completed=true` | Filter completed tasks |

---

## 📚 Dependencies You'll Install

```
fastapi          # Web framework
uvicorn          # ASGI server to run the app
pydantic         # Data validation (comes with FastAPI)
sqlalchemy       # Database ORM
pytest           # Testing framework
httpx            # HTTP client for testing
```

---

## 🚀 Learning Path (Step by Step)

1. **[NEXT]** Activate virtual environment & install FastAPI
2. Create `main.py` with a "Hello World" endpoint
3. Create the `Task` model with Pydantic
4. Implement in-memory CRUD (using a list)
5. Add proper error handling
6. Connect SQLite database
7. Refactor to use SQLAlchemy
8. Add async operations
9. Write tests
10. Add filtering/searching

---

## 💡 Tips for Your Interview

1. **Explain your thought process** - Don't just write code, explain WHY
2. **Mention trade-offs** - "I used SQLite for simplicity, but for production I'd use PostgreSQL"
3. **Reference this project** - "In my Task Manager API, I implemented..."
4. **Know the basics deeply** - They'll ask about decorators, generators, type hints

---

## ❓ Common Interview Questions This Project Prepares You For

- What is a decorator? Can you write one?
- Explain type hints in Python
- What's the difference between a list and a tuple?
- How does `async/await` work?
- What is a generator? When would you use `yield`?
- How do you handle exceptions in Python?
- What is ORM? Why use SQLAlchemy?
- How do you test Python applications?

---

*Let's start building! Your teacher is ready to guide you.* 🐍
