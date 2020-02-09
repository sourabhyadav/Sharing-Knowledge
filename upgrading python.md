## How to upgrade python 2.7 to python 3.x

**Install Python 3.6** [here][1]  

**Error solution for 'add-repository** [here][2]


In Ubuntu 16.04 default python is 2.7 and defaults python3 is 3.5. But if you want to install python 3.6 or above I found few seps you need to follow as given below.  

```
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.5 1
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.6 2
```
The above command wil install an additional python to your system. Say now you will have ```2.7```, ```3.5``` and ```3.6``` in your ```/usr/bin/```.
System gives you the liberty to choose which python you wanted to continue using below command:
``
sudo update-alternatives --config python3
```

Ater this you can check your python version using:
```
$ python3 -V
Python 3.6.9
```  


[1]: https://askubuntu.com/questions/865554/how-do-i-install-python-3-6-using-apt-get/865569#865569  
[2]: http://lifeonubuntu.com/ubuntu-missing-add-apt-repository-command/
