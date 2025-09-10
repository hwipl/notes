# Getmail

Getmail configuration file in `~/.getmail/getmailrc`, that is used to retrieve
mails from POP3 mailbox with SSL and pass it to Dovecot, delete old mails from
server after 3 years, write log to `~/.getmail/getmail.log`:

```
[retriever]
type = SimplePOP3SSLRetriever
server = SERVER
username = USER
password = PASS

[destination]
type = MDA_external
# path = /usr/local/libexec/dovecot/deliver
path = /usr/lib/dovecot/deliver
arguments = ("-e",)

[options]
read_all = false
delete = false
delete_after = 1095
received = false
delivered_to = false
message_log = ~/.getmail/getmail.log
```

## Cron Job with File Locking

Make sure only one instance of getmail is running at the same time with
`flock`:

```console
$ EDITOR=vim crontab -e
# retrieve mails every 5 minutes
*/5 * * * * flock -n ~/.getmail/getmail.lock getmail -q -g ~/.getmail/ -r getmailrc
```

## Systemd Timer

Only one instance of getmail is running at the same time with systemd timer.
TODO: add
