# gorok

A simple tool for taking stdin and passing a grok pattern over it to convert it to JSON and send back out to stdout.

## examples

```
$ head /var/log/syslog | ./gorok --pattern="%{SYSLOGBASE}"   
{"HOSTNAME":"czarknado","HOUR":"13","IP":"","IPORHOST":"czarknado","IPV4":"","IPV6":"","MINUTE":"29","MONTH":"May","MONTHDAY":"14","SECOND":"11","SYSLOGBASE":"May 14 13:29:11 czarknado colord[1324]:","SYSLOGFACILITY":"","SYSLOGPROG":"colord[1324]","TIME":"13:29:11","facility":"","logsource":"czarknado","pid":"1324","priority":"","program":"colord","timestamp":"May 14 13:29:11"}
{"HOSTNAME":"czarknado","HOUR":"13","IP":"","IPORHOST":"czarknado","IPV4":"","IPV6":"","MINUTE":"29","MONTH":"May","MONTHDAY":"14","SECOND":"26","SYSLOGBASE":"May 14 13:29:26 czarknado anacron[1171]:","SYSLOGFACILITY":"","SYSLOGPROG":"anacron[1171]","TIME":"13:29:26","facility":"","logsource":"czarknado","pid":"1171","priority":"","program":"anacron","timestamp":"May 14 13:29:26"}
```

