## Practice based Docker learnings. It includes Docker concepts, commands and important links to solve issues.

**Install Docker:**

**Add user group to the docker:**
* This helps to remove sudo dependencies for running docker command

**Change path of default docker:**
* Since docker images eats up your system memory, you can decide which partition to use for docker say /mnt or /home etc.

**Adding correct dns setting for docker container**
* This helps in soving issues related to apt-get update not working.
* How to get correct dns IP from your PC

**Creating shared folder between docker container and actual PC**
* Since docker creates its own vitual machine and space it might happen that once the image is deleted it will free-up all the space automatically. 
TO avoid this we can create a shared directory that even if docker image is deleted our saved stuff like trained models, result images etc. should still be with us.

