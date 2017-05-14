# Go Grok Yourself

A simple tool for taking stdin and passing a grok pattern over it to convert it to JSON and send back out to stdout.

## examples

### Basic command line usage:

```
$ head /var/log/syslog | ./gogrokyourself --pattern="%{SYSLOGBASE}"   
{"HOSTNAME":"czarknado","HOUR":"13","IP":"","IPORHOST":"czarknado","IPV4":"","IPV6":"","MINUTE":"29","MONTH":"May","MONTHDAY":"14","SECOND":"11","SYSLOGBASE":"May 14 13:29:11 czarknado colord[1324]:","SYSLOGFACILITY":"","SYSLOGPROG":"colord[1324]","TIME":"13:29:11","facility":"","logsource":"czarknado","pid":"1324","priority":"","program":"colord","timestamp":"May 14 13:29:11"}
{"HOSTNAME":"czarknado","HOUR":"13","IP":"","IPORHOST":"czarknado","IPV4":"","IPV6":"","MINUTE":"29","MONTH":"May","MONTHDAY":"14","SECOND":"26","SYSLOGBASE":"May 14 13:29:26 czarknado anacron[1171]:","SYSLOGFACILITY":"","SYSLOGPROG":"anacron[1171]","TIME":"13:29:26","facility":"","logsource":"czarknado","pid":"1171","priority":"","program":"anacron","timestamp":"May 14 13:29:26"}
```

### Use in a docker image:

The following will add the binary (once built) into the apache image and pipe the apache ouput through `gogrokyourself`

```
$ docker build . -f Dockerfile-apache -t apache-grok
$ docker run -ti -p 8080:80 apache-grok
...
...
{"BASE10NUM":"45","COMMONAPACHELOG":"172.17.0.1 - - [14/May/2017:20:57:10 +0000] \"GET / HTTP/1.1\" 200 45","EMAILADDRESS":"","EMAILLOCALPART":"","HOSTNAME":"","HOUR":"20","INT":"+0000","IP":"172.17.0.1","IPV4":"172.17.0.1","IPV6":"","MINUTE":"57","MONTH":"May","MONTHDAY":"14","SECOND":"10","TIME":"20:57:10","USER":"-","USERNAME":"-","YEAR":"2017","auth":"-","bytes":"45","clientip":"172.17.0.1","httpversion":"1.1","ident":"-","rawrequest":"","request":"/","response":"200","timestamp":"14/May/2017:20:57:10 +0000","verb":"GET"}
{"BASE10NUM":"45","COMMONAPACHELOG":"172.17.0.1 - - [14/May/2017:20:57:14 +0000] \"GET / HTTP/1.1\" 200 45","EMAILADDRESS":"","EMAILLOCALPART":"","HOSTNAME":"","HOUR":"20","INT":"+0000","IP":"172.17.0.1","IPV4":"172.17.0.1","IPV6":"","MINUTE":"57","MONTH":"May","MONTHDAY":"14","SECOND":"14","TIME":"20:57:14","USER":"-","USERNAME":"-","YEAR":"2017","auth":"-","bytes":"45","clientip":"172.17.0.1","httpversion":"1.1","ident":"-","rawrequest":"","request":"/","response":"200","timestamp":"14/May/2017:20:57:14 +0000","verb":"GET"}


