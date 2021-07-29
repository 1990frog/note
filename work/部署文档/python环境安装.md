[[TOC]]

FROM java:8
WORKDIR /app
COPY *.jar /app/
COPY start.sh /app/
RUN nohup java -jar /app/pig-register.jar &
RUN nohup java -jar /app/pig-gateway.jar &
RUN nohup java -jar /app/pig-auth.jar &
RUN nohup java -jar /app/pig-umps-biz.jar &
ENTRYPOINT ["tail","-f","nohup.out"]



docker run -d --network=host -v /etc/hosts:/etc/hosts --name pig pig tail -f /dev/null