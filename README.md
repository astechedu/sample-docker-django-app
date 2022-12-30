# Dockerized Django App

This is sample docker django app.


# Dockerfile 

    FROM python:3.8
    RUN apt-get update \
      && apt-get install -y --no-install-recommends \
                    #postgresql-client \	
      && rm -rf /var/lib/apt/lists/*

    WORKDIR /usr/src/app
    COPY requirements.txt ./
    RUN pip install -r requirements.txt
    COPY . .

    EXPOSE 8000
    CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]



#Building image

	docker build . -t dockerized_django

#Running container

	docker run --name django-app -p 8080:80 -d dockerized_django

	
