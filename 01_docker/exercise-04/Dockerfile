FROM python:3.10.0-slim

LABEL maintainer="trainer@xebia.com"

COPY . /app
WORKDIR /app

# TODO: revert order
RUN pip install -r requirements.txt

EXPOSE 5000

ENTRYPOINT ["python"]
CMD ["app.py"]
