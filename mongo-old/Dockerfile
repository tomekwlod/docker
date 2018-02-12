FROM mongo:3.2.9
COPY setup.sh /setup.sh
RUN /setup.sh


# https://github.com/docker-library/mongo/issues/49
# https://github.com/nanoninja/docker-nginx-php-mongo nice examples + https://github.com/nanoninja/php-fpm/blob/master/Dockerfile as a PHP-FPM Dockerfile
# https://stackoverflow.com/questions/41861908/cant-connect-to-docker-mongodb
# https://stackoverflow.com/questions/33558506/how-to-create-a-mongo-docker-image-with-default-collections-and-data


# FROM mongo:3.2.9

# # Modify child mongo to use /data/db2 as dbpath (because /data/db wont persist the build)
# RUN mkdir -p /data/db2 \
#     && echo "dbpath = /data/db2" > /etc/mongodb.conf \
#     && chown -R mongodb:mongodb /data/db2

# COPY . /data/db2

# RUN mongod --fork --logpath /var/log/mongodb.log --dbpath /data/db2 --smallfiles \
#     && CREATE_FILES=/data/db2/scripts/*-create.js \
#     && for f in $CREATE_FILES; do mongo 127.0.0.1:27017 $f; done \
#     && INSERT_FILES=/data/db2/scripts/*-insert.js \
#     && for f in $INSERT_FILES; do mongo 127.0.0.1:27017 $f; done \
#     && mongod --dbpath /data/db2 --shutdown \
#     && chown -R mongodb /data/db2

# # Make the new dir a VOLUME to persists it 
# VOLUME /data/db2

# CMD ["mongod", "--config", "/etc/mongodb.conf", "--smallfiles"]