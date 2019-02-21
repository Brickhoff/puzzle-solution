# Solution for Insight DevOps Engineering Systems Puzzle

# Fixed Bugs
1. The flask server is runnig on its default port 5000. This information is found on [this Flask API document](http://flask.pocoo.org/docs/1.0/api/).So I modified the nginx file and dockerfile so that they are using port 5000 now instead of 5001.

2. From Puzzzle details part in README, we can know that port 8080 should be on the host side. From `conf.d/flaskapp.conf` we know that nginx is running on port 80, which means port 80 should be opened on the container. Therefore, the port used in nginx congfiguration in `docker-compose.yml` is wrong since "80:8080" means the port 80 on the host must be forwarded to port 8080 on the container. By changing "80:8080" to "8080:80", the bug is fixed.

3. After fixing the two bugs above, the web is up and running on `localhost:8080`. I tried to submit a item to test the website, but the successful page is only returned with an empty array `[]`. I tried to submit another item, the array `[,]` is returned. Thererfore, I located the problem in `success route` in `app.py`. I modified some of the code and the items can be returned in json format now.


