# foundation

## How to run 
```
$ cd ~ 
$ mkdir Projects
$ cd Projects
$ git clone git@github.com:dev360/foundation.git
```

- Install [Docker Desktop](https://www.docker.com/products/docker-desktop)

- To start docker and get into the shell:
```
$ docker-compose run --rm foundation bash
```
- To start the server, do:
```
docker-compose run --rm --service-ports foundation python manage.py runserver
```

**Please note:** I did not create any django project, you have to get into the shell 
of this docker image and run `django-admin.py`, or otherwise follow the django tutorials.


## Useful Django commands:
- Connect to the database: `python manage.py dbshell`
- Python shell to interact with the Django models: `python manage.py shell`
- Create database migrations: `python manage.py makemigrations`
- Run the database migrations: `python manage.py migrate`


## Getting around the shell, and interacting with the Django ORM:
- `dir()` on an object can display what attributes and functions are available.
- To inspect a django model's available fields, do:
  ```
  Author._meta.fields
  ```
- Get one: 
  ```
  Author.objects.get(id=1)
  ```
- Get all:
  ```
  Author.objects.all()
  ```
- Filter: 
  ```
  Author.objects.filter(first_name='Christian')
  ```
- Create/update: 
  ```
  author = Author()
  author.first_name = ...
  ...
  author.save()
  ```
- Delete:
  ```
  author = Author.objects.get(id=...)
  author.delete()
  ```
- Delete multiple:
  ```
  ids = [1, 2, 3, 4]
  author = Author.objects.filter(id__in=ids).delete()
  ```
- Get, or create if doesn't exist:
  ```
  author, created = Author.objects.get_or_create(email='xxxxx@gmail', defaults=dict(first_name='John', last_name='Doe'))
  ```

