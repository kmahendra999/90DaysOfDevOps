## Day 16 Task: Docker for DevOps Engineers.


### Docker
 Docker is a software platform that allows you to build, test, and deploy applications quickly. Docker packages software into standardized units called containers that have everything the software needs to run including libraries, system tools, code, and runtime. Using Docker, you can quickly deploy and scale applications into any environment and know your code will run.

# Tasks

 As you have already installed docker in previous days tasks, now is the time to run Docker commands.

- Use the `docker run` command to start a new container and interact with it through the command line. [Hint: docker run hello-world]

<pre>
 [root@node5 ~]# docker run -dit --name test1 httpd
Unable to find image 'httpd:latest' locally
latest: Pulling from library/httpd
af107e978371: Already exists 
eba4da411ea0: Pull complete 
4f4fb700ef54: Pull complete 
ed4d6291a6c2: Pull complete 
b42c390e1de9: Pull complete 
eafe388a0bb8: Pull complete 
Digest: sha256:f0a93744d8006e6f7ee5086c9ddccdcfa33d1091f15269a00547b4c382459c1f
Status: Downloaded newer image for httpd:latest
789331277a64c1e74d2e2d096efe266caeca9eb24a63feef7e33fde0f452b377
[root@node5 ~]# docker ps -a
CONTAINER ID   IMAGE         COMMAND              CREATED              STATUS                          PORTS     NAMES
789331277a64   httpd         "httpd-foreground"   3 seconds ago        Up 2 seconds                    80/tcp    test1

</pre>

- Use the `docker inspect` command to view detailed information about a container or image.
<pre>
 [root@node5 ~]# docker inspect --type=container awesome_visvesvaraya
[
    {
        "Id": "144f843c1f6826223ce629dab62218d5d308186014f074a4106e6d36b1fd1d5a",
        "Created": "2024-01-03T08:23:56.945594268Z",
        "Path": "httpd-foreground",
        "Args": [],
        "State": {
            "Status": "running",
            "Running": true,
            "Paused": false,
            "Restarting": false,
            "OOMKilled": false,
            "Dead": false,
            "Pid": 4445,
            "ExitCode": 0,
            "Error": "",
            "StartedAt": "2024-01-03T08:23:57.585563556Z",
            "FinishedAt": "0001-01-01T00:00:00Z"
        },
        "Image": "sha256:6fd77d7e5eb732dacab601d4556c04a6c312928fb8989fe3b0a47d82db772441",
        "ResolvConfPath": "/var/lib/docker/containers/144f843c1f6826223ce629dab62218d5d308186014f074a4106e6d36b1fd1d5a/resolv.conf",
        "HostnamePath": "/var/lib/docker/containers/144f843c1f6826223ce629dab62218d5d308186014f074a4106e6d36b1fd1d5a/hostname",
        "HostsPath": "/var/lib/docker/containers/144f843c1f6826223ce629dab62218d5d308186014f074a4106e6d36b1fd1d5a/hosts",
        "LogPath": "/var/lib/docker/containers/144f843c1f6826223ce629dab62218d5d308186014f074a4106e6d36b1fd1d5a/144f843c1f6826223ce629dab62218d5d308186014f074a4106e6d36b1fd1d5a-json.log",
        "Name": "/awesome_visvesvaraya",
        "RestartCount": 0,
        "Driver": "overlay2",
        "Platform": "linux",
        "MountLabel": "",
        "ProcessLabel": "",
        "AppArmorProfile": "",
        "ExecIDs": null,
        "HostConfig": {
            "Binds": null,
            "ContainerIDFile": "",
            "LogConfig": {
                "Type": "json-file",
                "Config": {}
            },
            "NetworkMode": "default",
            "PortBindings": {},
            "RestartPolicy": {
                "Name": "no",
                "MaximumRetryCount": 0
            },
            "AutoRemove": false,
            "VolumeDriver": "",
            "VolumesFrom": null,
            "ConsoleSize": [
                37,
                140
            ],
            "CapAdd": null,
            "CapDrop": null,
            "CgroupnsMode": "host",
            "Dns": [],
            "DnsOptions": [],
            "DnsSearch": [],
            "ExtraHosts": null,
            "GroupAdd": null,
            "IpcMode": "private",
            "Cgroup": "",
            "Links": null,
            "OomScoreAdj": 0,
            "PidMode": "",
            "Privileged": false,
            "PublishAllPorts": false,
            "ReadonlyRootfs": false,
            "SecurityOpt": null,
            "UTSMode": "",
            "UsernsMode": "",
            "ShmSize": 67108864,
            "Runtime": "runc",
            "Isolation": "",
            "CpuShares": 0,
            "Memory": 0,
            "NanoCpus": 0,
            "CgroupParent": "",
            "BlkioWeight": 0,
            "BlkioWeightDevice": [],
            "BlkioDeviceReadBps": [],
            "BlkioDeviceWriteBps": [],
            "BlkioDeviceReadIOps": [],
            "BlkioDeviceWriteIOps": [],
            "CpuPeriod": 0,
            "CpuQuota": 0,
            "CpuRealtimePeriod": 0,
            "CpuRealtimeRuntime": 0,
            "CpusetCpus": "",
            "CpusetMems": "",
            "Devices": [],
            "DeviceCgroupRules": null,
            "DeviceRequests": null,
            "MemoryReservation": 0,
            "MemorySwap": 0,
            "MemorySwappiness": null,
            "OomKillDisable": false,
            "PidsLimit": null,
            "Ulimits": null,
            "CpuCount": 0,
            "CpuPercent": 0,
            "IOMaximumIOps": 0,
            "IOMaximumBandwidth": 0,
            "MaskedPaths": [
                "/proc/asound",
                "/proc/acpi",
                "/proc/kcore",
                "/proc/keys",
                "/proc/latency_stats",
                "/proc/timer_list",
                "/proc/timer_stats",
                "/proc/sched_debug",
                "/proc/scsi",
                "/sys/firmware",
                "/sys/devices/virtual/powercap"
            ],
            "ReadonlyPaths": [
                "/proc/bus",
                "/proc/fs",
                "/proc/irq",
                "/proc/sys",
                "/proc/sysrq-trigger"
            ]
        },
        "GraphDriver": {
            "Data": {
                "LowerDir": "/var/lib/docker/overlay2/755d7fa44ad86e5afaab4c8259d6532670fb1cfb59157b8b0d520f1b49db8329-init/diff:/var/lib/docker/overlay2/952f4a6bb9a7e386678ff6569208141487e89ec022d2073c835a69ac4ab94cbe/diff:/var/lib/docker/overlay2/520c3ac3799bb2024c04a0c4aee9cd39c8b501c549a3aaad19c0c974a21852c2/diff:/var/lib/docker/overlay2/99078cce1163bbd809c049e139b30762a14a650251fc62259bc727a8541339fd/diff:/var/lib/docker/overlay2/778949a9116e286a6e09153acbd898ba226e574a09e770fab9063abb22a874bd/diff:/var/lib/docker/overlay2/1b118c6b770787aedc123a8ab38af2428f17247e4ca4f42f79b9204180571ffa/diff:/var/lib/docker/overlay2/8ccd519736486e031db9f55780c1e915f6238ff91150d02c0bb2f67b528d057b/diff",
                "MergedDir": "/var/lib/docker/overlay2/755d7fa44ad86e5afaab4c8259d6532670fb1cfb59157b8b0d520f1b49db8329/merged",
                "UpperDir": "/var/lib/docker/overlay2/755d7fa44ad86e5afaab4c8259d6532670fb1cfb59157b8b0d520f1b49db8329/diff",
                "WorkDir": "/var/lib/docker/overlay2/755d7fa44ad86e5afaab4c8259d6532670fb1cfb59157b8b0d520f1b49db8329/work"
            },
            "Name": "overlay2"
        },
        "Mounts": [],
        "Config": {
            "Hostname": "144f843c1f68",
            "Domainname": "",
            "User": "",
            "AttachStdin": false,
            "AttachStdout": false,
            "AttachStderr": false,
            "ExposedPorts": {
                "80/tcp": {}
            },
            "Tty": true,
            "OpenStdin": true,
            "StdinOnce": false,
            "Env": [
                "PATH=/usr/local/apache2/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                "HTTPD_PREFIX=/usr/local/apache2",
                "HTTPD_VERSION=2.4.58",
                "HTTPD_SHA256=fa16d72a078210a54c47dd5bef2f8b9b8a01d94909a51453956b3ec6442ea4c5",
                "HTTPD_PATCHES="
            ],
            "Cmd": [
                "httpd-foreground"
            ],
            "Image": "httpd",
            "Volumes": null,
            "WorkingDir": "/usr/local/apache2",
            "Entrypoint": null,
            "OnBuild": null,
            "Labels": {},
            "StopSignal": "SIGWINCH"
        },
        "NetworkSettings": {
            "Bridge": "",
            "SandboxID": "f73c7e2d34fd05ce9f5a15389ac5b35b05414490630e0eaaadacdd13736629ff",
            "HairpinMode": false,
            "LinkLocalIPv6Address": "",
            "LinkLocalIPv6PrefixLen": 0,
            "Ports": {
                "80/tcp": null
            },
            "SandboxKey": "/var/run/docker/netns/f73c7e2d34fd",
            "SecondaryIPAddresses": null,
            "SecondaryIPv6Addresses": null,
            "EndpointID": "3d0c06adeffd54ad711ea2e0cea8c630fed4d08572bb6bfc5f3ea79510a3c26e",
            "Gateway": "172.17.0.1",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "IPAddress": "172.17.0.2",
            "IPPrefixLen": 16,
            "IPv6Gateway": "",
            "MacAddress": "02:42:ac:11:00:02",
            "Networks": {
                "bridge": {
                    "IPAMConfig": null,
                    "Links": null,
                    "Aliases": null,
                    "NetworkID": "36ecff57b2058f80e1acb82cfbb123c4896cb3d5d5dadc7072783c4df9d0ae05",
                    "EndpointID": "3d0c06adeffd54ad711ea2e0cea8c630fed4d08572bb6bfc5f3ea79510a3c26e",
                    "Gateway": "172.17.0.1",
                    "IPAddress": "172.17.0.2",
                    "IPPrefixLen": 16,
                    "IPv6Gateway": "",
                    "GlobalIPv6Address": "",
                    "GlobalIPv6PrefixLen": 0,
                    "MacAddress": "02:42:ac:11:00:02",
                    "DriverOpts": null
                }
            }
        }
    }
]

</pre>

- Use the `docker port` command to list the port mappings for a container.

<pre>
[root@node5 ~]# docker run -dit --name=apachecontainer1 -p 8081:80 httpd:latest
2840c45b5a86dc5b1ba404fc241b74ad781fae8410f7118737b61ae27614418e

[root@node5 ~]# docker port apachecontainer1
80/tcp -> 0.0.0.0:8081
80/tcp -> [::]:8081
[root@node5 ~]# 

 
</pre>

- Use the `docker stats` command to view resource usage statistics for one or more containers.

<pre>
[root@node5 ~]# docker stats apachecontainer1
 CONTAINER ID   NAME               CPU %     MEM USAGE / LIMIT     MEM %     NET I/O       BLOCK I/O   PIDS
2840c45b5a86   apachecontainer1   0.01%     6.816MiB / 1.706GiB   0.39%     2.63kB / 0B   0B / 0B     82

</pre>

- Use the `docker top` command to view the processes running inside a container.

<pre>
 [root@node5 ~]# docker top apachecontainer1
UID                 PID                 PPID                C                   STIME               TTY                 TIME                CMD
root                4818                4799                0                   00:29               pts/0               00:00:00            httpd -DFOREGROUND
33                  4841                4818                0                   00:29               pts/0               00:00:00            httpd -DFOREGROUND
33                  4842                4818                0                   00:29               pts/0               00:00:00            httpd -DFOREGROUND
33                  4843                4818                0                   00:29               pts/0               00:00:00            httpd -DFOREGROUND
[root@node5 ~]# 

</pre>

- Use the `docker save` command to save an image to a tar archive.

<pre>
 [root@node5 ~]# docker run -dit --name=con1 httpd:latest
ac7149205c99c7dd60c52c151099cf1d4f45f424e95e0a7f684858284f96a9ea

[root@node5 ~]# docker ps -a
CONTAINER ID   IMAGE          COMMAND              CREATED          STATUS                      PORTS     NAMES
ac7149205c99   httpd:latest   "httpd-foreground"   30 seconds ago   Exited (0) 15 seconds ago             con1

 [root@node5 ~]# docker exec -it con1 /bin/bash
 
      root@ac7149205c99:/usr/local/apache2/htdocs# cat index.html 
      <html><body><h1>It works!</h1></body></html>
      root@ac7149205c99:/usr/local/apache2/htdocs# echo "Hello again checked, it's worked" >> index.html 
      root@ac7149205c99:/usr/local/apache2/htdocs# cat index.html 
      <html><body><h1>It works!</h1></body></html>
      Hello again checked, it's worked
      root@ac7149205c99:/usr/local/apache2/htdocs# read escape sequence
      [root@node5 ~]# docker ps
      CONTAINER ID   IMAGE          COMMAND              CREATED         STATUS         PORTS     NAMES
      ac7149205c99   httpd:latest   "httpd-foreground"   5 minutes ago   Up 4 minutes   80/tcp    con1

[root@node5 ~]# docker commit con1 mycustonhttpd:latest
sha256:b9451f4b3e5166849fd96a26f52bcae5ceafad766db6947668371b24819d6343

[root@node5 ~]# docker save -o mycustomhttpdimage.tar.gz mycustonhttpd:latest

[root@node5 ~]# ls
anaconda-ks.cfg  Desktop  Documents  Downloads  Music  mycustomhttpdimage.tar.gz  original-ks.cfg  Pictures  Public  Templates  Videos

[root@node5 ~]# docker load -i mycustomhttpdimage.tar.gz 
d128c8f47469: Loading layer [==================================================>]  5.632kB/5.632kB
Loaded image: mycustonhttpd:latest
[root@node5 ~]# docker images
REPOSITORY        TAG       IMAGE ID       CREATED         SIZE
mycustonhttpd     latest    b9451f4b3e51   6 minutes ago   167MB


</pre>

- Use the `docker load` command to load an image from a tar archive.

These tasks involve simple operations that can be used to manage images and containers. 

For reference you can watch this video:
https://youtu.be/Tevxhn6Odc8

You can Post on LinkedIn and let us know what you have learned from this task by #90DaysOfDevOps Challange. Happy Learning :)
