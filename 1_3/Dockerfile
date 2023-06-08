FROM python:3.9-slim

WORKDIR /app

RUN groupadd --gid 1000 appgrp \
    && useradd --uid 1000 --gid 1000 -m appusr

COPY --chown=appusr:appgrp ./1_2/getweather ./1_2/requirements.txt ./

RUN pip install --no-cache-dir -r /app/requirements.txt

RUN chmod +x /app/getweather

USER appusr

CMD [ "./getweather" ]