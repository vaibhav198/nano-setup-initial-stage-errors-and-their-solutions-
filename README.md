# nano-setup-initial-stage-errors-and-their-solutions-
This repo contains probably all the errors that we might face when we will be installing a new nano along with their solution


# 1. when you trying to run ```./camera_client``` 
If you encountered with ```error while loading shared libraries: libyajl.so.2: cannot open shared object file: no such file or directory```

# Solution
```sudo apt install libyajl-dev```

# 2. eth0 ip is not static

Now, you need to set the static ip. So how to setup static ip----
1. first run ```nmcli connection```
2. Now you can all the connection here, you need to edit the wired connection. To do this you need to run ```sudo nmcli connections edit Wir....``` after capital w press "tab" for autocompletion. (make sure you have selected wired network)
3. Now you will get nmcli prompt, now run ```print ipv4```
4. Now run ```set ipv4.addresses 192.168.1.1/16```
5. now ```save```
6. ```ctrl+d```

