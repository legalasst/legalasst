**Before performing the following operations, you need to ensure that Docker and NVIDIA-Docker are installed**
<br>The file download address：[https://drive.google.com/drive/folders/1we6H70vxXPwkDls0W2P65Zuavka_hscU?usp=drive_link](https://drive.google.com/drive/folders/1we6H70vxXPwkDls0W2P65Zuavka_hscU?usp=drive_link)<br/>
The following is how to operate the downloaded `legal_asst_fe.tar` and `web_server_2.zip` files
<a name="aQrdf"></a>
#### web_server_2.zip
```bash
# step 1
unzip web_server_2.zip

# step 2
docker load -i web_server.tar

# step 3 find web_server.tar IMAGE ID
docker images 
# REPOSITORY        TAG                             IMAGE ID       CREATED        SIZE
# <none>            <none>                          73bb5c3c2591   9 months ago   18.6GB

# step 3 
docker run --gpus all -d -p 5008:5008 73bb5c3c2591 #  73bb5c3c2591 use your imageid

# step 4 
docker ps -a
# CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS                    PORTS                                                  NAMES
# eae5d46f6682   73bb5c3c2591   "/bin/sh -c 'nohup p…"   4 seconds ago   Up 3 seconds              0.0.0.0:5008->5008/tcp, :::5008->5008/tcp              blissful_kapitsa
```
<a name="ZwL2M"></a>
#### legal_asst_fe.tar
```bash
# step 1
docker load -i legal_asst_fe.tar

#step 2 find legal_asst_fe.tar IMAGE ID
docker images  
# REPOSITORY        TAG                             IMAGE ID       CREATED        SIZE
# <none>            <none>                          805af5a56438   8 months ago   30MB

# step 3 WEB_CONTROLLER_MULTI_AGENT_HOST use your host
docker run -d -p 1000:3000 --env WEB_CONTROLLER_MULTI_AGENT_HOST=xx.xx.xx.xx --env WEB_CONTROLLER_MULTI_AGENT_PORT=5008 805af5a56438  #  805af5a56438 use your imageid

# step 4
docker ps -a
# CONTAINER ID   IMAGE          COMMAND                  CREATED         STATUS                     PORTS                                                  NAMES
# f129f6e625a7   805af5a56438   "/bin/sh -c 'envsubs…"   6 seconds ago   Up 5 seconds               80/tcp, 0.0.0.0:1000->3000/tcp, :::1000->3000/tcp      happy_lumiere

```
<a name="fAYkH"></a>
#### Access your_host:1000
![image.png](https://cdn.nlark.com/yuque/0/2023/png/25608060/1691824394038-173f1a58-60f5-491d-88bc-2f0eb0803b7c.png#averageHue=%233c3b3a&clientId=u703b32a2-9f28-4&from=paste&height=639&id=u9c362437&originHeight=959&originWidth=1914&originalType=binary&ratio=1.5&rotation=0&showTitle=false&size=302629&status=done&style=none&taskId=ufb9ade8f-3650-4fbb-b6e4-de10683a50d&title=&width=1276)
