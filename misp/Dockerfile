FROM python:3.7.4-alpine3.10

# Copy the connector
COPY src /opt/opencti-connector-misp

# Install Python modules
# hadolint ignore=DL3003
RUN apk --no-cache add git build-base && \
    cd /opt/opencti-connector-misp && \
    pip3 install --no-cache-dir git+https://github.com/OpenCTI-Platform/client-python@master && \
    pip3 install --no-cache-dir -r requirements.txt && \
    apk del git build-base

# Expose and entrypoint
COPY entrypoint.sh /
RUN chmod +x /entrypoint.sh
ENTRYPOINT ["/entrypoint.sh"]
