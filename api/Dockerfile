# # base image
# FROM python:3.8

# # setup environment variable
# ENV DockerHOME=/home/app/webapp

# # set work directory
# RUN mkdir -p $DockerHOME
# # where your code lives
# WORKDIR $DockerHOME

# # set environment variables
# ENV PYTHONDONTWRITEBYTECODE 1
# ENV PYTHONUNBUFFERED 1

# # install dependencies
# RUN pip install --upgrade pip
# RUN pip install virtualenv

# # copy whole project to your docker home directory.
# COPY . $DockerHOME

# RUN virtualenv env
# RUN . env/bin/activate

# # run this command to install all dependencies
#  pip install -r requirements.txt

# RUN python manage.py migrate
# # port where the Django app runs
# EXPOSE 8000
# # start server
# CMD python manage.py runserver

# We Use an official Python runtime as a parent image
FROM python:3.8

# Allows docker to cache installed dependencies between builds
COPY requirements.txt requirements.txt
RUN pip install --no-cache-dir -r requirements.txt

# Mounts the application code to the image
COPY . code
WORKDIR /code

EXPOSE 8000

# runs the production server
ENTRYPOINT ["python", "manage.py"]
CMD ["runserver", "0.0.0.0:8000"]