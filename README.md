https://blog.csdn.net/ydm19891101/article/details/104505624/
ps -ef|grep python | grep -v grep |  awk '{print $2}' | xargs -t kill -9 
