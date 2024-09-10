ARG MONGO_VER

FROM mongo:${MONGO_VER}

COPY /auth/mongodb-keyfile /data
RUN chmod 400 /data/mongodb-keyfile
RUN chown 999:999 /data/mongodb-keyfile
RUN apt-get update
RUN apt-get install -y iputils-ping net-tools