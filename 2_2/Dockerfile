FROM python:3.9-slim

WORKDIR /app

RUN apt-get -y update \
    && apt-get -y install nmap \
    && groupadd --gid 1000 appgrp \
    && useradd --uid 1000 --gid 1000 -m appusr

COPY --chown=appusr:appgrp ./2_1/scanner ./2_2/requirements.txt ./

RUN pip install --no-cache-dir -r /app/requirements.txt \
    && mkdir /app/data \
    && chown appusr:appgrp -R /app/data \
    && chmod +x /app/scanner

USER appusr

ENTRYPOINT [ "./scanner" ]