FROM apache/airflow

USER root

RUN apt-get update \
  && apt-get full-upgrade -yqq \
  && apt-get install -yqq \
         make \
         gcc \
         libpq-dev \
  && apt-get autoremove -yqq --purge \
  && apt-get clean \
  && rm -rf /var/lib/apt/lists/* 

COPY --chown=airflow:root requirements.txt /tmp/

USER airflow

RUN pip install --no-cache-dir -r /tmp/requirements.txt

ENV AWS_ACCESS_KEY_ID=AKIARBH4BMKZMHIAYPLQ
ENV AWS_SECRET_ACCESS_KEY=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
ENV S3_BUCKET='bancodoutorado'

COPY --chown=airflow:root . /opt/airflow/dags
