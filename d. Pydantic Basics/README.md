# Pydantic — Introduction

| Concept                  | Description / Example |
|--------------------------|------------------------|
| **What is Pydantic?**    | A Python library for data validation and settings management using Python type hints. |
| **Core Idea**            | Define models with types → Pydantic auto-validates and converts data. |
| **Installation**         | `pip install pydantic` |
| **Basic Model**          | ```python<br>from pydantic import BaseModel<br><br>class User(BaseModel):<br>    id: int<br>    name: str<br>    age: int = 18<br><br>u = User(id="1", name="Alice")<br>print(u)  # id=1 name='Alice' age=18``` |
| **Validation**           | Automatically converts types (e.g., `"1"` → `int`) and raises errors for invalid data. |
| **Default Values**       | Fields can have defaults (`age=18` above). |
| **Nested Models**        | Models can contain other models for complex data structures. |
| **Use Cases**            | API input validation, config management, enforcing data integrity. |

⚡ **Key Benefit:** Clean, Pythonic, type-driven data validation without manual checks.
