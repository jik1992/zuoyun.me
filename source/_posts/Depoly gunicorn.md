title: Depoly gunicorn
date: 2015/11/19 17:19:43
categories:

 - python 


tags:

- tryghost

---

nginx+gunicorn+flask

http://gunicorn.org/#quickstart

使用很简单

```language-bash
  $ sudo pip install virtualenv
  $ mkdir ~/environments/
  $ virtualenv ~/environments/tutorial/
  $ cd ~/environments/tutorial/
  $ ls
  bin  include  lib
  $ source bin/activate
  (tutorial) $ pip install gunicorn
  (tutorial) $ mkdir myapp
  (tutorial) $ cd myapp/
  (tutorial) $ vi myapp.py
  (tutorial) $ cat myapp.py

  def app(environ, start_response):
      data = "Hello, World!\n"
      start_response("200 OK", [
          ("Content-Type", "text/plain"),
          ("Content-Length", str(len(data)))
      ])
      return iter([data])

  (tutorial) $ ../bin/gunicorn -w 4 myapp:app
  [2014-09-10 10:22:28 +0000] [30869] [INFO] Listening at: http://127.0.0.1:8000 (30869)
  [2014-09-10 10:22:28 +0000] [30869] [INFO] Using worker: sync
  [2014-09-10 10:22:28 +0000] [30874] [INFO] Booting worker with pid: 30874
  [2014-09-10 10:22:28 +0000] [30875] [INFO] Booting worker with pid: 30875
  [2014-09-10 10:22:28 +0000] [30876] [INFO] Booting worker with pid: 30876
  [2014-09-10 10:22:28 +0000] [30877] [INFO] Booting worker with pid: 30877
```

然后 nginx 再反代一下就好了

tornado



