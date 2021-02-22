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
6. ```ctrl+d``` to come out from nmcli prompt
Now, reboot the nano.

# 3. If you trying to run the pipeline on newly setuped nano and your pipeline is getting killed then you need to do following things
1. See the output of ```free -m``` and then ```df -h``` Now you can see, not enough swap memory.
2. two things to do---
2.a: ```sudo vim /etc/systemd/nvzramconfig.sh``` . Here try to find out the line, starting with mem=$... . In that line try to remove / 2.
2.b: Once 2.a is done, then pull https://github.com/JetsonHacksNano/installSwapfile this repo. ```git clone https://github.com/JetsonHacksNano/installSwapfile```
2.c: After pulling the repo, go to the directory 'installSwapfile'. from within that directory, run: ```sudo ./installSwapFile.sh```
2.d: Now reboot the nano


# Some additional information
-> nano has two power mode one is 5W and other one 10W. <br>
-> to set power mode one can use ```sudo nvpmodel -m 0``` for 10W and ```sudo nvpmodel -m 1``` for 5W. <br>
-> to enable clock one can run ```sudo jetson_clocks``` or one can do this with ```jtop``` (to run ```jtop```, you need to install jetson stats, to install it run ```sudo pip3 install -U jetson-stats```, in jtop goto 5th window and press ```s``` to enable jetson clocks and press ```e``` to enable it automatically on boot time.


