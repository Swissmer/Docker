FROM nginx

WORKDIR /home/

COPY nginx.conf /etc/nginx/nginx.conf
COPY run.sh .

RUN apt-get update && apt-get install -y gcc spawn-fcgi libfcgi-dev; \
    chown -R nginx:nginx /etc/nginx/nginx.conf; \
    chown -R nginx:nginx /var/cache/nginx; \
    chown -R nginx:nginx /home; \
    touch /var/run/nginx.pid; \
    chown -R nginx:nginx /var/run/nginx.pid; \
    rm -rf /var/lib/apt/lists
RUN rm -f /usr/bin/umount /usr/sbin/unix_chkpwd /usr/bin/chage /usr/bin/expiry /usr/bin/newgrp /usr/bin/passwd /usr/bin/chsh /usr/bin/su /usr/bin/chfn /usr/bin/mount /usr/bin/gpasswd /usr/bin/wall

USER nginx

ENTRYPOINT ["sh", "./run.sh"]
HEALTHCHECK NONE
