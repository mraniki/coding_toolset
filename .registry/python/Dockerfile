FROM python:3.13
WORKDIR /app
COPY ./examples/ /.requirements/requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt
EXPOSE 8080
CMD [ "python", "./example.py" ]