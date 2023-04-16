FROM python:3.10-bullseye

LABEL MAINTANER="Jonas Geschonke <jonas.geschonke@gmx.de>"

ENV GROUP_ID=1000
ENV USER_ID=1000

WORKDIR /app

ADD ./requirements.txt /app/requirements.txt
RUN pip install -r requirements.txt
ADD . /app/
RUN pip install gunicorn

# RUN addgroup --gid $GROUP_ID app
# RUN adduser --default --uid $USER_ID --group app app --shell /bin/sh

# USER app

EXPOSE 5000

CMD [ "gunicorn", "-w", "4", "--bind", "0.0.0.0:5000", "wsgi"]