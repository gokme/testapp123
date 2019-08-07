# Steps to build a docker image
FROM centos:7
MAINTAINER gokul.sampath@amadeus.com
RUN yum -y update
RUN yum -y install httpd

#COPY
#COPY code/* /var/www/html         
#COPY code/code.zip /var/www/html         - Copy the file

#ADD
ADD code /var/www/html
#ADD code/code.zip /var/www/html -- Unzip the file and copy
#ADD https://amadeus.com/code.zip /var/www/html -- Directly download it from artifactory and Unzip the file and copy.
#COPY AND ADD HAS ABOVE differences.

# EVN - Environment Variables - sometimes used to specify the backend information
# Default varible can be set and it act as a ENV variable.
ENV BACKEND=test

#EXPOSE
#By default goes into metadata.
# PORT 0 -65535
EXPOSE 80

#USER - By default docker cmd runs as root. 
# You need to install a user and use the user 
# USER apache
# do some work 
# Change user by USER root
#WORKDIR
#VOLUME - Not recommended on docker file. Its not a best practice.

COPY config/httpd-foreground /usr/bin
RUN chmod 755 /usr/bin/httpd-foreground

# CMD - CMD does not execute while you build, it just stores in metadata
# JSON ITEM to make sure it running as the process 1 and monitored by docker.
# Rather than shell and apache, it runs as apache
CMD ["httpd-foreground"]
# CMD Vs ENTRYPOINT
# CMD can be overridden on Command line, ENTRYPOINT cannot be overridden on command line


#ENTRYPOINT