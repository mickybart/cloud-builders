FROM gcr.io/cloud-builders/gcloud-slim

# Install kubectl. gcloud's component manager is disabled, so we have to
# install it from apt-get.
# Official documentation: https://kubernetes.io/docs/tasks/tools/install-kubectl/#install-kubectl
RUN apt-get update \
    && apt-get install -y apt-transport-https \
    && curl -s https://packages.cloud.google.com/apt/doc/apt-key.gpg | apt-key add \
    && echo "deb https://apt.kubernetes.io/ kubernetes-xenial main" > /etc/apt/sources.list.d/kubernetes.list \
    && apt-get update \
    && apt-get install -y kubectl \
    && rm -rf /var/lib/apt/lists/*

COPY kubectl.bash /builder/kubectl.bash

ENTRYPOINT ["/builder/kubectl.bash"]
