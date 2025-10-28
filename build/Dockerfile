FROM openspeedtest/latest

ARG UID
ARG GID
ARG TIMEZONE

RUN /bin/sh -c apk update

RUN /bin/sh -c apk add shadow sudo tzdata

RUN /bin/sh -c groupadd -g ${GID} container

RUN /bin/sh -c useradd -m -u ${UID} -g container admin

RUN /bin/sh -c echo "admin ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/admin

RUN /bin/sh -c chmod 0440 /etc/sudoers.d/admin

RUN /bin/sh -c ln -sf /usr/share/zoneinfo/${TIMEZONE} /etc/localtime

USER admin

CMD ["/entrypoint.sh"]