# Use an official Python runtime as the base image
FROM python:3.11-slim

# Clone the qdrant repository
RUN sed -i 's/deb.debian.org/mirrors.aliyun.com/g' /etc/apt/sources.list.d/debian.sources && apt-get update && apt-get install -y git
RUN git clone https://github.com/oxidized-world/svgo-rs.git qdrant

# Set the working directory in the container
WORKDIR /app

# Copy the requirements file into the container
COPY requirements.txt .

# Install the required packages
RUN pip install --upgrade pip  -i https://pypi.tuna.tsinghua.edu.cn/simple
RUN pip install -r requirements.txt  -i https://pypi.tuna.tsinghua.edu.cn/simple

# Copy the Python files into the container
COPY src ./src

COPY run.sh .

ENTRYPOINT ["./run.sh"]
