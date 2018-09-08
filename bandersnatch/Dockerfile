FROM python:3.6-slim-stretch

RUN apt-get update \
    && apt-get -y upgrade  \
    && apt-get -y dist-upgrade \
    && apt-get -y install --no-install-recommends \
        software-properties-common \
        python3-pip \
        cron \
        git-core \
        procps \
        vim \
    && apt clean \
    && apt autoremove -y \
    && pip install --trusted-host pypi.python.org virtualenv zc.buildout \
    && git clone https://github.com/pypa/bandersnatch \
    && cd bandersnatch \
    && ./bootstrap.sh

COPY bandersnatch.conf /etc/
COPY bandersnatchcron /etc/cron.d/

RUN crontab /etc/cron.d/bandersnatchcron

CMD ["cron", "-f"]