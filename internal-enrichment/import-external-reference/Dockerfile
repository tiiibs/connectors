FROM python:3.9-alpine

# Copy the connector
COPY src /opt/opencti-connector-import-external-reference

# Install Python modules
# hadolint ignore=DL3003
RUN apk --no-cache add git build-base libmagic libffi-dev libxml2-dev libxslt-dev openssl-dev rust cargo jpeg-dev zlib-dev wkhtmltopdf && \
    cd /opt/opencti-connector-import-external-reference && \
    pip3 install --no-cache-dir -r requirements.txt && \
    apk del git build-base

# Expose and entrypoint
COPY entrypoint.sh /
RUN chmod +x /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
