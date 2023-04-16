FROM python:3.10

LABEL MAINTANER="Jonas Geschonke <jonas.geschonke@gmx.de>"

ENV GROUP_ID=1000\USER_ID=1000

WORKDIR /var/app

ADD ./requirements.txt /var/app/requirements.txt
RUN pip install -r requirements.txt
ADD . /var/app/
RUN pip install gunicorn

RUN addgroup -g $GROUP_ID app
RUN adduser -D -u $USER_ID -G app app -s /bin/sh

USER app

EXPOSE 5000

CMD [ "gunicorn", "-w", "4", "--bind", "0.0.0.0:5000", "wsgi"]