# openvas 9
    docker run --name openvas -p 80:80 -p 9390:9390 -d a1exei/a1exei:openvas-9

This will grab the container from the docker registry and start it up. Openvas startup can take some time (4-5 minutes while NVT's are scanned and databases rebuilt), so be patient. Once you see a It seems like your OpenVAS-9 installation is OK. process in the logs, the web ui is good to go. Goto http://<machinename>
You can configure the proxy (nginx) in front of the container and configure HTTPS in it.

    Username: admin
    Password: admin
To check the status of the process, run:

    docker top openvas
In the output, look for the process scanning cert data. It contains a percentage.

To run bash inside the container run:

    docker exec -it openvas bash

# Set Admin Password
The admin password can be changed by specifying a password at runtime using the env variable OV_PASSWORD:

    docker run --name openvas -e OV_PASSWORD=admin -p 80:80 -p 9390:9390 -d a1exei/a1exei:openvas-9

# Thanks
Thanks for the great tutorial: mikesplain https://github.com/mikesplain/openvas-docker
I changed port 80 in the container and enabled HTTP_ONLY = 1
