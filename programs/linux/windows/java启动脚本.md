

start.bat
```bat
set local=%CLIN_HOME%
echo %local%
start javaw -Dfile.encoding=utf-8 -jar %local%\pig-register.jar
start javaw -Dfile.encoding=utf-8 -jar %local%\pig-gateway.jar
start javaw -Dfile.encoding=utf-8 -jar %local%\pig-auth.jar
start javaw -Dfile.encoding=utf-8 -jar %local%\pig-upms-biz.jar
exit
```