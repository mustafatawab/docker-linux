FROM python:3.12

LABEL maintainer="mustafa"

WORKDIR /code

COPY . /code/
 
RUN pip install uv

RUN uv add  "fastapi[standard]" 

EXPOSE 8000

CMD ["uv", "run", "fastapi", "dev", "main.py", "--reload"]
