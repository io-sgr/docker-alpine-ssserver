# docker-alpine-ssserver
Tiny image which brings you a Shadowsocks server using shadowsocks-libev

# Usage

1. Create a Shadowsocks server configuration file at **<some_path>/ss-server.json** for example, with content:
```
{
    "server":"<server_ip>",
    "server_port":8888,
    "local_port":1080,
    "password":"<password>",
    "timeout":180,
    "method":"<encryption>"
}
```
The server needs to listen at port **8888** because that's the port that docker image exposed. You will able to map it to a different port later. DO NOT change this port unless you know what you are doing.

2. Run the following command:
```
docker run -d \
    -p <actual_port>:8888 \
    -v <some_path>/ss-server.json:/etc/shadowsocks-libev/config.json \
    sgrio/alpine-ssserver
```
3. Now you have a Shadowsocks server listening at the **actual_port** you just passed to the command.
