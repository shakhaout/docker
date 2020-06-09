# docker
Commands for pulling up docker containers in ubuntu

1. First install docker on ubuntu

2. This will pull an image instance for tensorflow 2 inside docker:
   >> $ sudo docker pull nvcr.io/nvidia/tensorflow:20.03-tf2-py3
   >> $ sudo docker run --gpus all -it --rm -v $(pwd):/workspace nvcr.io/nvidia/tensorflow:20.03-tf2-py3
   
3. These commands have to run to save & exit docker image:
   - Press Ctrl p
   - Press Ctrl q
   >> $ sudo docker ps 
   - Copy the ID of the latest running image
   >> $ sudo docker commit ID name         (any name i.e. hossain)

4. Command to start container image in the present working directory where it was pulled up:
   - open a terminal in the present working directory then run this command
   >> $ sudo docker run --gpus all -it --rm -v $(pwd):/workspace hossain
   
5. If it is required to run jupyter notebook in within docker then run these commands:
   >> $ sudo docker run --gpus all -it -p 8080:8080 --rm -v $(pwd):/workspace hossain
   >> $ jupyter notebook --ip 0.0.0.0 --no-browser --port 8080 --allow-root
   - from browser go to this url: 
     localhost:8080/tree
   - Enter password: copy paste token from terminal
6. Finally after finishing work repeat process number (3) then run this command to stop all containers:
   >> $ sudo docker stop $(sudo docker ps -aq)

