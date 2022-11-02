# OpenConnect-VPN-Server
**2022 NOV UPDATE**: We dockerized and added Dockerfile to run it anywhere you want on any linux distro easily.
Buggy script for configuring OpenConnect (ocserv 1.1.6) protocol on the server easily and automatically.

Tested on ubuntu 18.04 and 16.04 and 22.04.

## Docker Installation
1. Install Docker
```bash
sudo apt update
```
```bash
sudo apt install apt-transport-https ca-certificates curl software-properties-common
```
```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
```
```bash
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
```bash
sudo apt update
```
```bash
apt-cache policy docker-ce
```
```bash
sudo apt install docker-ce
```
2. Build docker image
```bash
docker build -t ocserv https://github.com/vecatime/OcServ-1.1.6-On-Ubuntu.git
```

3. Run docker container
```bash
docker run --name ocserv --privileged -p 443:443 -p 443:443/udp -d ocserv
```

4. Add user
```bash
docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd testUserName
```

5. Change user password
```bash
docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd testUserName
```

6. Delete user
```bash
docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd -d testUserName
```

7. Lock user
```bash
docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd -l testUserName
```

8. Unlock user
```bash
docker exec -ti ocserv ocpasswd -c /etc/ocserv/ocpasswd -u testUserName
```

9. Show all users and their hashed password
```bash
docker exec -ti ocserv cat /etc/ocserv/ocpasswd
```

## Features
- Easy install
- Easy uninstall
- Add User
- Change Password
- Show All Users
- Delete User
- Lock User
- Unlock User

## How to connect to it?
For making connection to your server, you can use `AnyConnect`, `OpenConnect` or other alternative clients.

- AnyConnect: [GUI AnyConnect client for available platforms](https://it.umn.edu/vpn-downloads-guides).
- OpenConnect: [OpenConnect client for Linux](https://computingforgeeks.com/how-to-connect-to-vpn-server-with-openconnect-ssl-vpn-client-on-linux/).

And one more thing, contributions are welcome.

## More
The script is based on [here](https://ocserv.gitlab.io/www/recipes-ocserv-configuration-basic.html)
