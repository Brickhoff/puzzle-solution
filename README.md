# Solution for Insight DevOps Engineering Systems Puzzle

## Fixed Bugs
1. The flask server is runnig on its default port 5000. This information is found on [this Flask API document](http://flask.pocoo.org/docs/1.0/api/).So I modified the nginx file and dockerfile so that they are using port 5000 now instead of 5001.

2. From Puzzzle details part in README, we can know that port 8080 should be on the host side. From `conf.d/flaskapp.conf` we know that nginx is running on port 80, which means port 80 should be opened on the container. Therefore, the port used in nginx congfiguration in `docker-compose.yml` is wrong since "80:8080" means the port 80 on the host must be forwarded to port 8080 on the container. By changing "80:8080" to "8080:80", the bug is fixed.

3. After fixing the two bugs above, the web is up and running on `localhost:8080`. I tried to submit a item to test the website, but the successful page is only returned with an empty array `[]`. I tried to submit another item, the array `[,]` is returned. Thererfore, I located the problem in `success route` in `app.py`. I modified some of the code and the items can be returned in json format now.

## Comments
I don't know about others, but the most challenging part for me is actually install Docker！ ╮(╯﹏╰）╭

I received the challenege on 02/20/2019 and I tried to do it at that night. My computer OS is Windows 10 home, so I cannot use the Docekr Desktop to install docker and I need to use Docekr Toolbox. The instrucation is pretty clear so I followed it. 

Things went badly after I installed the toolbox and VM Virtubox. I encountered the error "Setting env" first. After hous of searching on Google, I fixed it and felt so excited. However, after I tried to run docker, another error popped up and then another. After many times of uninstalling, reinstalling, changding code in `star.sh`, I somehow installed docker by using Kitematic. I was thrilled! I cloned the repo, run the command that is given in README. Everthing went smoothly until the error "Invalid volumn specification". I followed every method online but I can't fix it.

The next day, I went to the Student Computer Center in TAMU and I found that it's Windows 10 Enterprise! I tried to install it but it needs administrator's permission and I cannot get it from the IT department. I was devastated...(〒︿〒)

In the afternoon, I went to my friend's house and borrowed his Macbook Pro. The installation is so smooth and effertless!!!

The debug process is actually much easier compare to the installation process. It just needs me to be careful and use Goolge wisely. I am quite surprised that there is no bug in `postgres db` since the README suggests that we neew to familiar ourselves with `Docker, nginx, Flask, and Postgres`.

Since I don't wnat to congiurate the Github environment in his computer and I commited some changes in that computer, the first three commits are under his github name LMAO. After I realized this situation, I sent the files to my computer and commited correctly.

Anyway, I fixed those bugs in time. (Thankfully. The deadline is pretty short for me. I don't have time after today due to school and other stuff.)