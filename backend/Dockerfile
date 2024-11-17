FROM python:3.8-slim
WORKDIR /code
ADD . /code

# Install necessary dependencies and setup apt
RUN apt-get update || echo "Failed to update apt-get" && \
    echo "deb http://deb.debian.org/debian/ stable main" > /etc/apt/sources.list && \
    apt-get update && \
    apt-get install -y gcc libpq-dev default-libmysqlclient-dev && \
    apt-get clean && \
    rm -rf /var/lib/apt/lists/*

# Install Python dependencies
RUN pip install --no-cache-dir --trusted-host mirrors.aliyun.com -i https://mirrors.aliyun.com/pypi/simple/ supervisor && \
    pip install --no-cache-dir --trusted-host mirrors.aliyun.com -i https://mirrors.aliyun.com/pypi/simple/ -r ./requirements.txt



EXPOSE 80
ENTRYPOINT ["/bin/bash","-C","/code/backend/start.sh"]
