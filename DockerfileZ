FROM node:10.16

# set inotify and start the node application, replace yar with your command
RUN echo "#!/bin/sh \n\
echo "fs.inotify.max_user_watches before update" \n\
cat /etc/sysctl.conf\n\
echo "______________________________________________updating inotify ____________________________________" \n\
echo fs.inotify.max_user_watches=524288 | tee -a /etc/sysctl.conf && sysctl -p \n\
echo "updated value is" \n\
cat /etc/sysctl.conf | grep fs.inotify \n\
exec yarn start:dev \
" >> /usr/local/bin/entrypoint.sh

RUN chmod +x /usr/local/bin/entrypoint.sh

# EXPOSE TARGET PORT
EXPOSE 3001
ENTRYPOINT ["/usr/local/bin/entrypoint.sh"]

