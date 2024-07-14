<p align="center">
<img src ="https://spectralops.io/wp-content/uploads/2023/04/image4-3.png">
</p>

---

<p align="center">
<h1> Basic authentication </h1>
</p>

- In this project, you will learn what the authentication process means and implement Basic Authentication on a simple API.
  In the industry, you should not implement your own Basic authentication system and use a module or framework that does it for you (like in Python-Flask: Flask-HTTPAuth). Here, for learning purposes, we will walk through each step of this mechanism to understand it by doing.

<h1> Resources </h1>

Read or watch:

- [REST API Authentication Mechanisms](https://www.youtube.com/watch?v=501dpx2IjGY)
- [Base64 in Python](https://www.tutorialspoint.com/python3/python_base64.htm)
- [HTTP header Authorization](https://developer.mozilla.org/en-US/docs/Web/HTTP/Headers/Authorization)
- [Flask Base64 - concept](https://flask-httpauth.readthedocs.io/en/latest/)

---

<h1> Tasks </h1>

0. **Simple-basic-API**

   - **Task:** Download and start the project from the provided [`archive.zip`](https://intranet.alxswe.com/rltoken/2o4gAozNufil_KjoxKI5bA). Set up and start the server using the given instructions. Use the API to make a request, for example, by running the provided `curl` command. Ensure the server responds correctly, and the API is functional.
   - **Files:** [requirements.txt](./requirements.txt), [api/v1/app.py](./api/v1/app.py), [api/v1/views/index.py](./api/v1/views/index.py)

1. **Error handler: Unauthorized**

   - **Task:** Add a new error handler for HTTP status code 401 in `api/v1/app.py`. The response must be a JSON with the message: {"error": "Unauthorized"}. Use Flask's `jsonify` for this task. Also, create a new endpoint in `api/v1/views/index.py` with the route GET /api/v1/unauthorized that raises a 401 error using `abort(401)`.
   - **Files:** [api/v1/app.py](./api/v1/app.py), [api/v1/views/index.py](./api/v1/views/index.py)

2. **Error handler: Forbidden**

   - **Task:** Add a new error handler for HTTP status code 403 in `api/v1/app.py`. The response must be a JSON with the message: {"error": "Forbidden"}. Use Flask's `jsonify` for this task. Also, create a new endpoint in `api/v1/views/index.py` with the route GET /api/v1/forbidden that raises a 403 error using `abort(403)`.
   - **Files:** [api/v1/app.py](./api/v1/app.py), [api/v1/views/index.py](./api/v1/views/index.py)

3. **Auth class**

   - **Task:** Create a new folder `api/v1/auth`, and within it, create an empty file `api/v1/auth/__init__.py`. Create the class `Auth` in the file `api/v1/auth/auth.py` with three public methods: `require_auth`, `authorization_header`, and `current_user`.
   - **Files:** [api/v1/auth/**init**.py](./api/v1/auth/__init__.py), [api/v1/auth/auth.py](./api/v1/auth/auth.py)

4. **Define which routes don't need authentication**

   - **Task:** Update the method `require_auth` in `Auth` to return True if the path is not in the list of excluded paths. Ensure the method is slash tolerant. Test the implementation using the provided examples.
   - **File:** [api/v1/auth/auth.py](./api/v1/auth/auth.py)

5. **Request validation!**

   - **Task:** Implement request validation in `api/v1/app.py`. Update the method `authorization_header` in `Auth` to handle request validation. Use Flask's `before_request` method to filter each request and raise appropriate errors (401 or 403) if validation fails.
   - **File:** [api/v1/app.py](./api/v1/app.py), [api/v1/auth/auth.py](./api/v1/auth/auth.py)

6. **Basic auth**

   - **Task:** Create a class `BasicAuth` that inherits from `Auth`. Update `api/v1/app.py` to use `BasicAuth` based on the value of the environment variable `AUTH_TYPE`.
   - **Files:** [api/v1/app.py](./api/v1/app.py), [api/v1/auth/basic_auth.py](./api/v1/auth/basic_auth.py)

7. **Basic - Base64 part**

   - **Task:** Add a method `extract_base64_authorization_header` in `BasicAuth` that extracts the Base64 part of the Authorization header for Basic Authentication. Test the implementation using the provided examples.
   - **File:** [api/v1/auth/basic_auth.py](./api/v1/auth/basic_auth.py)

8. **Basic - Base64 decode**

   - **Task:** Add a method `decode_base64_authorization_header` in `BasicAuth` that decodes the Base64 string. Test the implementation using the provided examples.
   - **File:** [api/v1/auth/basic_auth.py](./api/v1/auth/basic_auth.py)

9. **Basic - User credentials**

   - **Task:** Add a method `extract_user_credentials` in `BasicAuth` that extracts user email and password from the Base64 decoded value. Test the implementation using the provided examples.
   - **File:** [api/v1/auth/basic_auth.py](./api/v1/auth/basic_auth.py)

10. **Basic - User object**

    - **Task:** Add a method `user_object_from_credentials` in `BasicAuth` that returns the User instance based on email and password. Test the implementation using the provided examples.
    - **File:** [api/v1/auth/basic_auth.py](./api/v1/auth/basic_auth.py)

11. **Basic - Overload current_user - and BOOM!**

    - **Task:** Overload the `current_user` method in `BasicAuth` to use the `user_object_from_credentials` method. Ensure that the API is now fully protected by Basic Authentication.
    - **File:** [api/v1/auth/basic_auth.py](./api/v1/auth/basic_auth.py)

> ## Advanced Tasks

12. **Logging Auth**

    - **Task:** Implement logging for the authentication process. Update the Auth class in the `api/v1/auth/auth.py` file to include logging statements at different stages of the authentication process. Log information such as when authentication is required, when it fails, and when it succeeds. Use the Python `logging` module for this purpose.

    - **Files:** [auth.py](./api/v1/auth/auth.py)

13. **Basic - Base64 encode**

    - **Task:** Add the method `def create_base64_authorization_header(self, email: str, pwd: str) -> str` in the class `BasicAuth`. This method should create a Base64-encoded string for Basic Authentication using the provided email and password. Ensure it follows the correct format.

    - **Files:** [basic_auth.py](./api/v1/auth/auth.py)

---

<h2> Author </h2>

- [`@Josh-techie`]() | Software Engineer Student

  > Reach out to me if you need any help or have any questions.

  <a href="mailto:youssef.abouyahia@e-polytechnique.ma">
  	<img alt="Feel free to contact me" src="https://img.shields.io/badge/-Ask_me_anything-blue?style=flat&logo=Gmail&logoColor=white&link=mailto:youssef.abouyahia@e-polytechnique.ma&color=3d85c6" />
  </a>
  <span> | </span>
    <a href="https://www.linkedin.com/in/youssef-abouyahia/">
        <img alt="Linkedin Profile" src="https://img.shields.io/badge/-Linkedin-0072b1?style=flat&logo=Linkedin&logoColor=white&link=https://www.linkedin.com/in/youssef-abouyahia/" />
    </a>
    <span> | </span>
    <a href="https://twitter.com/JoesephAb">
        <img alt="Twitter Profile" src="https://img.shields.io/badge/-Twitter-0072b1?style=flat&logo=Twitter&logoColor=white&link=https://twitter.com/JoesephAb&color=1DA1F2" />
    </a>