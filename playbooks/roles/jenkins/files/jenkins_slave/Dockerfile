FROM jaydp17/jenkins-slave

USER root

# Install curl
RUN apt-get update && apt-get install -y \
  curl \
  && rm -rf /var/lib/apt/lists/*

# Install docker client    
RUN curl -fsSL "https://download.docker.com/linux/static/stable/x86_64/docker-17.03.1-ce.tgz" \
  | tar -xzC /usr/local/bin --strip=1 docker/docker
