## Practice based Docker Documentation** 
It includes Docker concepts, commands and important links to solve issues.

**Install Docker:** [TODO]
* Installing docker 19.03 for all the latest updates. Bellow commands were tested on docker 19.03

**Install Docker with gpu (cuda) and Tensorflow:** [TODO]
* We can train deep learning models with gpu with docker itself

**Add user group to the docker:** [TODO]
* This helps to remove sudo dependencies for running docker command

**Change path of default docker:**
* Since docker images eats up your system memory, you can decide which partition to use for docker say /mnt or /home etc.
* This is required when you want to have more images which might take lot of your HW space.
* There are [2 methods][1] which is found till now link:

**Method 1:** 
* You can change Docker’s storage base directory (where container and images go) using the -g option when starting the Docker daemon.
Ubuntu/Debian: edit your /etc/default/docker file with the -g option: DOCKER_OPTS="-dns 8.8.8.8 -dns 8.8.4.4 -g /mnt"

After a restart, (service docker restart) Docker should use the new directory.

**Method 2:** (This worked for me)
* Using a symlink is another method to change image storage.

**Setps:**

    Stop docker: service docker stop. Verify no docker process is running ps faux
    
    Double check docker really isn’t running. 
    Take a look at the current docker directory: ls /var/lib/docker/
    
    Make a backup - tar -zcC /var/lib docker > /mnt/pd0/var_lib_docker-backup-$(date +%s).tar.gz
    
    Move the /var/lib/docker directory to your new partition: mv /var/lib/docker /mnt/pd0/docker
    
    Make a symlink: ln -s /mnt/pd0/docker /var/lib/docker
    
    Take a peek at the directory structure to make sure it looks like it did before the mv: ls /var/lib/docker/ (note the trailing slash to resolve the symlink)
    
    Start docker back up service docker start
    
    restart your containers



**Adding correct dns setting for docker container**
* When you run a docker contianer inside that contianer you will not be able to install or download anything from web. 
* This is probably because of firewal on your Host PC. 
* This helps in soving issues related to apt-get update not working.
* For this you need to provide correct dns setting for docker container to run.
```
sudo docker run -it --dns 10.47.56.129 tensorflow/tensorflow:devel-gpu

OR

sudo docker run -it --network=host tensorflow/tensorflow:devel-gpu 
```
* Note: You might ned to find correct dns for your system


**Creating shared folder between docker container and actual PC**
* Since docker creates its own virtual machine and space it might happen that once the image is deleted it will free-up all the space automatically. 
* To avoid this we can create a shared directory that even if docker image is deleted our saved stuff like trained models, result images etc. should still be with us.
* Docker creates voulmes for sharing the data between Host PC and docker container. To know more about docker volumes [read1][3] and [read2][2] 
* However the short answer is: use -v command
```
sudo docker run -it -v </absolute/path/of/Host PC>:</absolute/path/inside/container> tensorflow/tensorflow:devel-gpu bash
```
For example:
```
sudo docker run -it --dns 10.47.56.129 -v /home/jyadavso/sourabh/Play_n_n_Learn:/home/jyadavso/sourabh/Play_n_n_Learn tensorflow/tensorflow:devel-gpu bash
```
**Note:**
* When docker -v command sees a path which is already existing in your Host PC it does not creates a new voluume insde the docker/volume
* But docker -v sees a non-exiting path then it creates new volume inside the docker/volume directory and later link that volume to container path
For e.g.:
```
sudo docker run -it --dns 10.47.56.129 -v docker_share:/home/jyadavso/sourabh/Play_n_n_Learn tensorflow/tensorflow:devel-gpu bash
```
The above command will create a new volume inside the docker/volume and which will be shared with given container path. 
To verify that you can sunn ``` sudo docker volume list```

**Providing host IP to a docker container to watch the process from Host PC:** [TODO]
* With this we wont face internet connectivity problems when we are inside docker.
* A typical scenario happens that we wont be able to connect with pip install or apt-get install as by default internet wont be working inside the docker container.

**Install docker with Jupyter support:**
* We can rn docker with jupyter support on Host-PC browser
* Following are the steps:
```
sudo docker run -it --gpus all --dns 10.47.56.129 -p 8888:8888 --net=host  tensorflow/tensorflow:devel-gpu 
```
Here ```--net=host``` for providing the docker container mapped to host-pc. ```-p 8888:8888``` provides the port for jupyter server to map on Host-PC. This is optional as by defualt it will map to 8888 port.

For more details on running jupyter running on docker you can look [here][4] and [here][5]

**Container with display permissions:**
* Oftern it may happen that you will require to display images or other media inside the docker itself. 
* Say ```cv2.imsho(...)```, with default docker container you will face lot of related to ```X server``` or ```cannot connected to diplay``` etc.
* To avoid this you need to provide permissions to docker container to use display. Following is the command tou can use it:
```
$ xhost +
$ sudo docker run -it --gpus all --dns 10.47.56.129 -p 8888:8888 -v /home/jyadavso/sourabh/Play_n_n_Learn/CV_DL/trackers/SiamMask:/home/jyadavso/sourabh/Play_n_n_Learn/CV_DL/trackers/SiamMask --name cont_siamese_mask_disp -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=$DISPLAY --env QT_X11_NO_MITSHM=1 tensorflow/tensorflow:devel-gpu bash
```
* ```xhost +``` provides access to your X server to be used by others
* ``` -v /tmp/.X11-unix:/tmp/.X11-unix -e DISPLAY=$DISPLAY --env QT_X11_NO_MITSHM=1``` This command enables the permissions to use dispaly to the docker container. Rest all commands remains same.

[1]: https://forums.docker.com/t/how-do-i-change-the-docker-image-installation-directory/1169
[2]: https://linuxhint.com/docker_volume_share_data/
[3]: https://www.ionos.com/community/server-cloud-infrastructure/docker/understanding-and-managing-docker-container-volumes/
[4]: https://jupyter-docker-stacks.readthedocs.io/en/latest/using/running.html
[5]: https://github.com/ReproNim/neurodocker/issues/82
