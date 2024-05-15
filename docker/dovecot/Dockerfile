FROM alpine:latest

ENV USERNAME myuser
ENV PASSWORD change-me
ENV DOMAIN mail.svc.cluster.local

RUN apk update && apk add dovecot-pop3d

RUN addgroup dovecot mail

RUN chown -R root:mail /var/mail
RUN chmod -R g+rwx /var/mail

RUN adduser -S $USERNAME -G mail 

RUN echo "$USERNAME:{PLAIN}$PASSWORD:100:12::/home/$USERNAME" > /etc/dovecot/users

COPY local.conf /etc/dovecot/local.conf

EXPOSE 110 143 993 995

CMD ["dovecot", "-F"]
