FROM openspeedtest/latest

ARG UID
ARG GID
ARG TIMEZONE

RUN /bin/sh -c apk --no-cache update && apk add --no-cache shadow sudo tzdata

RUN /bin/sh -c groupadd -g ${GID} container && useradd -m -u ${UID} -g container admin

RUN /bin/sh -c echo "admin ALL=(ALL) NOPASSWD: ALL" > /etc/sudoers.d/admin && chmod 0440 /etc/sudoers.d/admin

RUN /bin/sh -c ln -sf /usr/share/zoneinfo/${TIMEZONE} /etc/localtime

USER admin

CMD ["/entrypoint.sh"]