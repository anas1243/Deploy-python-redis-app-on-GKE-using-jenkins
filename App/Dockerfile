FROM python:3.7
WORKDIR /app
# move project in working dir
ADD . /app
#set default env can overide this
ENV ENVIRONMENT=DEV
ENV PORT=8000
ENV REDIS_PORT=6379
ENV REDIS_DB=0
RUN pip install --upgrade pip
RUN pip install -r App/requirements.txt
CMD ["python", "App/hello.py"] 
