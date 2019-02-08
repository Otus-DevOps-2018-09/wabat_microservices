FROM gitlab/gitlab-runner:alpine

RUN echo "===> Installing sudo to emulate normal OS behavior..."  && \
    apk --update add sudo                                         && \
    \
    \
    echo "===> Adding Python runtime..."  && \
    apk --update add python py-pip openssl ca-certificates openssh py2-libcloud && \
    apk --update add --virtual build-dependencies \
                python-dev libffi-dev openssl-dev build-base       && \
    pip install --upgrade pip pycrypto cffi requests               && \
    \
    \
    echo "===> Installing Ansible..."  && \
    pip install ansible                && \
    \
    \
    echo "===> Removing package list..."  && \
    apk del build-dependencies            && \
    rm -rf /var/cache/apk/*               && \
    \
    \
    echo "===> Adding hosts for convenience..."  && \
    mkdir -p /etc/ansible                        && \
    echo 'localhost' > /etc/ansible/hosts


#COPY ansible-playbook-wrapper /usr/local/bin/
COPY  ansible.cfg /etc/ansible/
COPY  gce.py /etc/ansible/inventory/gce.py
ONBUILD  RUN  echo "===> Updating TLS certificates..."         && \
              apk --update add openssl ca-certificates

ONBUILD  WORKDIR  /tmp
ONBUILD  COPY  .  /tmp
ONBUILD  RUN  \
              echo "===> Diagnosis: host information..."  && \
              ansible -c local -m setup all


CMD ["run", "--user=gitlab-runner", "--working-directory=/home/gitlab-runner"]

#for gce.py
#apk add py2-libcloud
#pip pip install requests   
#ssh-cient

