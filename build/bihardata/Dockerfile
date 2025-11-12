FROM alpine:latest

# Use PYTHONUNBUFFERED=1 for live logs
ENV PYTHONUNBUFFERED=1

# 1. Install System Dependencies (Git, Python, pip, and build tools for psycopg2)
# cronie is installed for the cron service
RUN apk update && \
    apk add --no-cache \
        git \
        python3 \
        py3-pip \
        build-base \
        postgresql-dev \
        cronie && \
    rm -rf /var/cache/apk/*

# 2. Install Python Libraries
# Use the --break-system-packages flag to bypass the PEP 668 error
RUN pip3 install --no-cache-dir --break-system-packages \
    psycopg2-binary \
    pandas \
    requests

# 3. Application Setup
WORKDIR /app

# The following lines are for setting up the cronjob environment:
# (You will need to create these files in your project directory)
# COPY your_python_script.py /app/
# COPY your_crontab_file /etc/crontabs/root

# Set appropriate permissions for the crontab file
# RUN chmod 0644 /etc/crontabs/root

# 4. Command to run the cron daemon
# CMD ["crond", "-f"]
