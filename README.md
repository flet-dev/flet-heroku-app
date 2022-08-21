# Flet app hosted on Heroku

This is an example [Flet](https://flet.dev) app that can be deployed to Heroku as a web app.

Use this repository as a starting point for your own app.

In Heroku choose "GitHub" deployment method and select the repository.

A new deployment will automatically start on every push to the repository.

Key points to make Heroku work:

1. `Procfile` - nothing fancy, just running `python {your_program.py}` as a web process.
2. `requirements.txt` - the list of Python modules required by your program, including `flet`.
3. `main.py` - use TCP port binding provided by Heroku environment.

Heroku dynamically assigns your app a port and add its value to `PORT` environment variable.
To make Flet app using that port you should add `import os` to your Flet program and
modify `flet.app()` to use that port:

```python
import os

# the rest of your program

flet.app(target=main, port=os.getenv("PORT"))
```