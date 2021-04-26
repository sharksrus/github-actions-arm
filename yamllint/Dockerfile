FROM arm64v8/python:3.9-alpine

COPY yamllint.json /yamllint.json
COPY entrypoint.sh /entrypoint.sh

RUN pip install yamllint==1.26.0 --no-cache-dir \
    && chmod +x /entrypoint.sh

ENTRYPOINT ["/entrypoint.sh"]
CMD ["."]