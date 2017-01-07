
# ansible-builder-centos7
FROM openshift/base-centos7

MAINTAINER Robert Forsström <robert@middleware.se>

ENV BUILDER_VERSION 1.0

LABEL io.k8s.description="Platform for building images using Ansible Playbooks" \
      io.k8s.display-name="ansible-builder-centos7" \
      io.openshift.tags="builder,ansible,centos"

RUN yum install -y  epel-release && \
    yum install -y  ansible && \
    yum clean all -y

# TODO (optional): Copy the builder files into /opt/app-root
# COPY ./<builder_folder>/ /opt/app-root/

# Copy the S2I scripts to /usr/libexec/s2i, since openshift/base-centos7 image
# sets io.openshift.s2i.scripts-url label that way, or update that label

COPY ./.s2i/bin/ /usr/libexec/s2i

# TODO: Drop the root user and make the content of /opt/app-root owned by user 1001
# RUN chown -R 1001:1001 /opt/app-root

# This default user is created in the openshift/base-centos7 image
#USER 1001

# TODO: Set the default port for applications built using this image
# EXPOSE 8080

# TODO: Set the default CMD for the image
CMD ["usage"]
