mongodump \
--archive \
--gzip \
--host 106.75.59.253 \
--port 27017 \
--username caifu_openapi \
--password caifu_openapi.123 \
--authenticationDatabase caifu_openapi \
--db caifu_openapi \
 | mongorestore \
--drop \
--archive \
--gzip \
--host 127.0.0.1 \