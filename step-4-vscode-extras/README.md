Once you have successfully set up the remote connection, you can do many things with it. The foour most fun things that users prefer range from testing, building and running applications!


## ☸️ Building Application

The [/app](/app) directory has an application which we want to built and test in our remote enviroment to understand further steps! 

- Install Docker with the following script:
```bash
curl -fsSL https://get.docker.com | bash
```

In order to build and run the application in a remote environment, you will need to have Docker installed on your machine. You can download and install Docker from the official website: https://www.docker.com/ or with help of an script 

- Clone this Repo

Once you have Docker installed, you will need to clone the repository containing the application. You can do this by running the command `git clone https://github.com/hrittikhere/workshop-ec2-vscode` in the terminal.

```bash
hrittik@hrittik:~$ git clone https://github.com/hrittikhere/workshop-ec2-vscode
Cloning into 'workshop-ec2-vscode'...
remote: Enumerating objects: 189, done.
remote: Counting objects: 100% (189/189), done.
remote: Compressing objects: 100% (153/153), done.
remote: Total 189 (delta 60), reused 121 (delta 23), pack-reused 0
Receiving objects: 100% (189/189), 1.21 MiB | 47.60 MiB/s, done.
Resolving deltas: 100% (60/60), done.
```

![image](https://user-images.githubusercontent.com/67012359/214220763-a1f67342-d84e-4ba0-a03c-8bd82edbc436.png)

- Move to /app directory

After cloning the repository, navigate to the /app directory using the command `cd workshop-ec2-vscode/workshop-ec2-vscode/step-4-vscode-extras/app`

```bash
hrittik@hrittik:~$ cd workshop-ec2-vscode/step-4-vscode-extras/app/

hrittik@hrittik:~/workshop-ec2-vscode/step-4-vscode-extras/app$ ls
Dockerfile  README.md  deploy
```
![image](https://user-images.githubusercontent.com/67012359/214220819-206d911a-a972-4158-afcc-93eff94ff496.png)

- Docker build
 
 Once you have verified that the Dockerfile is correct, you can build the application by running the command `docker build -t [image-name] .` in the terminal.
 
 
 ```bash
 
hrittik@hrittik:~/workshop-ec2-vscode/step-4-vscode-extras/app$ docker build -t hrittik:test .
Sending build context to Docker daemon  14.34kB
Step 1/6 : FROM python:3.8-alpine
3.8-alpine: Pulling from library/python
8921db27df28: Pull complete 
3fd9832a787c: Pull complete 
6ce1e5a613ce: Pull complete 
75208903285a: Pull complete 
2bb0a9fec214: Pull complete 
Digest: sha256:28cd2bd2e3bc789817d7e55612db7430355bfcbb4633426abaf3f54a8db7da58
Status: Downloaded newer image for python:3.8-alpine
 ---> 9d5d37b3f167
Step 2/6 : COPY deploy/ /deploy
 ---> 67c407eaded7
Step 3/6 : WORKDIR /deploy
 ---> Running in 605e3a11301d
Removing intermediate container 605e3a11301d
 ---> 4bd40aa73ed5
Step 4/6 : RUN pip install -r requirements.txt
 ---> Running in 2079b372802d
Collecting click==8.0.3
  Downloading click-8.0.3-py3-none-any.whl (97 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 97.5/97.5 KB 1.1 MB/s eta 0:00:00
Collecting Flask==2.0.2
  Downloading Flask-2.0.2-py3-none-any.whl (95 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 95.2/95.2 KB 3.7 MB/s eta 0:00:00
Collecting itsdangerous==2.0.1
  Downloading itsdangerous-2.0.1-py3-none-any.whl (18 kB)
Collecting Jinja2==3.0.3
  Downloading Jinja2-3.0.3-py3-none-any.whl (133 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 133.6/133.6 KB 5.4 MB/s eta 0:00:00
Collecting MarkupSafe==2.0.1
  Downloading MarkupSafe-2.0.1-cp38-cp38-musllinux_1_1_x86_64.whl (30 kB)
Collecting Werkzeug==2.0.2
  Downloading Werkzeug-2.0.2-py3-none-any.whl (288 kB)
     ━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━ 288.9/288.9 KB 4.7 MB/s eta 0:00:00
Installing collected packages: Werkzeug, MarkupSafe, itsdangerous, click, Jinja2, Flask
Successfully installed Flask-2.0.2 Jinja2-3.0.3 MarkupSafe-2.0.1 Werkzeug-2.0.2 click-8.0.3 itsdangerous-2.0.1
Removing intermediate container 2079b372802d
 ---> 9d0b21465085
Step 5/6 : EXPOSE 5000
 ---> Running in acb1d8c29849
Removing intermediate container acb1d8c29849
 ---> 272d5d846c70
Step 6/6 : CMD ["python", "app.py", "--host=0.0.0.0"]
 ---> Running in 64ff32dca63a
Removing intermediate container 64ff32dca63a
 ---> 2241587c9499
Successfully built 2241587c9499
Successfully tagged hrittik:test
 
 ```

- Run Application

Finally, you can run the application by running the command `docker run -p [host-port]:[container-port] [image-name]` in the terminal. This will start the application and make it accessible on the specified host port.

```bash

hrittik@hrittik:~/workshop-ec2-vscode/step-4-vscode-extras/app$ docker run -p 5000:5000 hrittik:test
 * Serving Flask app 'app' (lazy loading)
 * Environment: production
   WARNING: This is a development server. Do not use it in a production deployment.
   Use a production WSGI server instead.
 * Debug mode: off
 * Running on all addresses.
   WARNING: This is a development server. Do not use it in a production deployment.
 * Running on http://172.17.0.2:5000/ (Press CTRL+C to quit)
172.17.0.1 - - [24/Jan/2023 05:43:37] "GET / HTTP/1.1" 200 -
172.17.0.1 - - [24/Jan/2023 05:43:37] "GET /static/style.css HTTP/1.1" 200 -
172.17.0.1 - - [24/Jan/2023 05:43:38] "GET /favicon.ico HTTP/1.1" 404 -

```

![image](https://user-images.githubusercontent.com/67012359/214220610-b13dfd68-f6e7-40f6-8aae-b0d2289f50c7.png)

## ⏩ Port Forwarding

You can also use the remote connection to forward a local port to a remote port, allowing you to access a service running on the remote host from your local machine. This can be useful for testing or debugging your application, as well as for accessing network resources that are not publicly accessible for temporary purpose.
![image](https://user-images.githubusercontent.com/67012359/214220499-a97ee7c0-4742-46c7-9efd-ded2b7aabfd1.png)

Use Ports section to map a new port! Now visit your browswer to access the port on your local host:

![image](https://user-images.githubusercontent.com/67012359/214220580-28196b98-07f8-490b-b165-c88aa2bf8292.png)


## 📂 File System Access

With the remote connection, you can access the file system of the remote host as if you were working directly on the machine. You can create, edit and delete files and directories, and use version control systems to manage your codebase.

Try uploading files to your remote server without any additional requirements!
