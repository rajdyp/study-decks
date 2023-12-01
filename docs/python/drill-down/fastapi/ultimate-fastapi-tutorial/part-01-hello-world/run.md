``` bash
#!/bin/sh

export APP_MODULE=${APP_MODULE-app.main:app}  # (1)
export HOST=${HOST:-0.0.0.0}  # (2)
export PORT=${PORT:-8001}

exec uvicorn --reload --host $HOST --port $PORT "$APP_MODULE"
```

1.  `${VAR-default}:` If VAR is unset `export APP_MODULE=${APP_MODULE}` or null, use the default value. Will treat an empty string as a valid value and not use the default. 
2.  `${VAR:-default}:` If VAR is unset or null, or set but empty, use the default value. Will include empty strings as cases where the default should be used.
