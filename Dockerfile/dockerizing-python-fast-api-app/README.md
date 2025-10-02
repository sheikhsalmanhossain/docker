## Python fast api app :

### Step 1: install FastAPI and uvicorn (server to run it):

``` pip install fastapi uvicorn ```

### Step 2: Create a simple FastAPI app :

Inside your project folder, create a file main.py:


```
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Hello, FastAPI from Docker!"}
```


### Run it locally:

``` python -m uvicorn main:app --reload --host 0.0.0.0 --port 8000 ```

Open browser at: http://127.0.0.1:8000
We can see output.


### Create requirements.txt:
``` pip freeze > requirements.txt ```


### Create a Dockerfile:

```
FROM python:3.11-slim
WORKDIR /app
COPY requirements.txt .
RUN pip install -r requirements.txt
COPY . .
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

### build dockerfile:
``` docker build -t my-py-app ```
### run container:
``` docker run -p 5000:8000 my-py-app ```

Now we can browse our app localhost:5000
