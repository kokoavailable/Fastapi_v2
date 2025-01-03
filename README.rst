FastAPI Server v2
=================

A **highly scalable and modular API server** built with **FastAPI**, implementing a **clean architecture approach** for **low coupling** and **high cohesion**. This project follows **best practices** for asynchronous programming, **integration with relational databases**, and **RESTful API design**.

The project is designed to handle complex domains and modules while maintaining a **clear separation of concerns**. By organizing code based on **domain-driven design (DDD)** principles, the structure remains **scalable**, **evolvable**, and **easy to maintain**.

--------------------------------------------------------------------------

Project Structure
-----------------

There are many ways to structure a project, but the best structure is one that is **consistent**, **straightforward**, and **predictable**.

Many example projects and tutorials divide the project by file type (e.g., ``crud``, ``routers``, ``models``), which works well for **microservices** or **small-scale projects**. However, for a **monolith** with **multiple domains and modules**, this approach becomes difficult to manage as the project grows.

This project adopts a structure inspired by **Netflix's Dispatch**, with some modifications to fit the needs of **complex domains**.

.. code-block:: text

    src/
    ├── auth/                 # Authentication & Authorization
    │   ├── router.py          # API Endpoints for authentication
    │   ├── schemas.py         # Pydantic models (Request/Response validation)
    │   ├── service.py         # Business logic for auth
    │   ├── models.py          # SQLAlchemy ORM models
    │   └── utils.py           # Utility functions (e.g., password hashing)
    ├── posts/                # Posts-related API module
    │   ├── router.py          # API Endpoints for posts
    │   ├── service.py         # Business logic for posts
    │   └── models.py          # ORM models for posts
    ├── database.py           # Database connection and session management
    ├── config.py             # Configuration (environment variables)
    └── main.py               # FastAPI app initialization

Design Philosophy and Patterns
------------------------------

This project follows key principles to maintain code quality and scalability:

* **Clean Architecture Approach**: Separation of layers such as API routes, services (business logic), and data access (repositories).
* **Domain-Driven Design (DDD)**: Organizing code by domains rather than file types to avoid tightly coupled structures.
* **Dependency Injection (DI)**: Using ``Depends()`` to inject dependencies into routes and services, improving testability and maintainability.
* **Service Layer Pattern**: Business logic is separated into service classes to prevent API routes from becoming bloated.
* **Repository Pattern**: Database access is abstracted through repository classes, keeping the service layer independent of ORM logic.

Key Features
------------

* **Asynchronous Processing**: FastAPI’s async capabilities ensure that the server can handle concurrent requests efficiently.
* **Centralized Configuration**: Environment variables are managed through ``.env`` files and Pydantic settings classes.
* **Auto-generated API Docs**: OpenAPI documentation available at ``/docs`` and ``/redoc`` for easy API exploration.
* **Linting and Formatting**: ``ruff`` and ``black`` are used to maintain consistent code style.

Installation and Setup
----------------------

1. **Clone the Repository**

   .. code-block:: bash

       git clone https://github.com/your-repo/fastapi-server-v2.git
       cd fastapi-server-v2

2. **Create a Virtual Environment**

   .. code-block:: bash

       python -m venv venv
       source venv/bin/activate  # Windows: venv\Scripts\activate

3. **Install Dependencies**

   .. code-block:: bash

       pip install -r requirements.txt

4. **Run Database Migrations**

   .. code-block:: bash

       alembic upgrade head

5. **Start the Development Server**

   .. code-block:: bash

       uvicorn src.main:app --reload

API Endpoints Overview
----------------------

.. list-table::
   :header-rows: 1
   :widths: 10 30 50

   * - Method
     - Endpoint
     - Description
   * - POST
     - ``/users/``
     - Create a new user
   * - POST
     - ``/auth/login/``
     - Log in to get a JWT token
   * - GET
     - ``/posts/{post_id}/``
     - Retrieve a specific post
   * - POST
     - ``/posts/``
     - Create a new post
   * - DELETE
     - ``/posts/{post_id}/``
     - Delete a specific post

Pre-commit Hooks
----------------

To maintain consistent code formatting and linting, pre-commit hooks are used with ``ruff`` and ``black``.

**Install Pre-commit Hooks**

.. code-block:: bash

   pre-commit install

**Run Pre-commit Hooks Manually**

.. code-block:: bash

   pre-commit run --all-files

Why This Structure?
-------------------

* **Modularity**: Each domain has its own folder containing routes, services, and models, making the structure easy to extend.
* **Scalability**: By following domain-driven design, the project is built to handle future feature additions with minimal impact on existing modules.
* **Consistency**: Code organization and naming conventions are consistent across the project, reducing cognitive load.

Feedback and Contributions
--------------------------

If you have suggestions or want to report an issue, feel free to open an issue or create a pull request! Your feedback helps make this project better.

Enjoy building with FastAPI Server v2! :rocket:

---------------------------------------------------------------------------

설명
----

- 이 문서는 **프로젝트 개요, 기능 설명, 설치 방법, API 사용법** 등을 포함하고 있습니다.
- **디자인 패턴과 철학**을 명시하여 프로젝트의 목적과 구조를 쉽게 이해할 수 있도록 작성하였습니다.
- 필요에 따라 **버전 정보**나 **추가 API 예제**를 포함해 확장할 수 있습니다.
- 추가적인 피드백이나 수정 사항이 있다면 언제든 알려주세요.
