# 1. Install Anaconda in Ubuntu 18.04 (VM - VirtualBox)
[Reference1](https://www.digitalocean.com/community/tutorials/how-to-install-the-anaconda-python-distribution-on-ubuntu-18-04)
[, Reference for other system](https://docs.anaconda.com/anaconda/install/)
```shell
$ cd /tmp
$ curl -O https://repo.anaconda.com/archive/Anaconda3-2019.03-Linux-x86_64.sh
$ sha256sum Anaconda3-2019.03-Linux-x86_64.sh
```
this will output, you can check the hash in [here](https://docs.anaconda.com/anaconda/install/hashes/lin-3-64/)
```shell
45c851b7497cc14d5ca060064394569f724b67d9b5f98a926ed49b834a6bb73a  Anaconda3-2019.03-Linux-x86_64.sh
```
Start to install packages
```shell
$ bash Anaconda3-2019.03-Linux-x86_64.sh
```
press "Enter" to read through the aggreement->and enter "yes" to aggree-> and press "Enter" to set install location<br/>
wait for it until it show up, and enter "yes" to initialize Anaconda3
```shell
Do you wish the installer to initialize Anaconda3
by running conda init? [yes|no]
[no] >>> yes
```
# 2. Install PyTorch
[Reference](https://pytorch.org/get-started/locally/)
```shell
$ conda install pytorch-cpu torchvision-cpu -c pytorch
```
# 3. Install numpy and Jupyter notebook
```shell
$ conda install numpy jupyter notebook
```

# 4. Clone the repository 
```shell
$ git clone https://github.com/udacity/deep-learning-v2-pytorch.git
```

# 5. Open jupyter notebook
```
$ cd deep-learning-v2-pytorch/
$ jupyter notebook
```
## Problem 1:
```shell
E: Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarily unavailable)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?
```
* Solve: 
    ```shell
    $ ps aux | grep -i apt
    root      2183  0.0  0.0   4628   848 ?        Ss   21:07   0:00 /bin/sh /usr/lib/apt/apt.systemd.daily install
    root      2187  0.0  0.0   4628  1680 ?        S    21:07   0:00 /bin/sh /usr/lib/apt/apt.systemd.daily lock_is_held install
    user_name    16339  0.0  0.0  21824  1016 pts/0    S+   21:18   0:00 grep --color=auto -i apt
    $ sudo kill 2183
    $ sudo kill 2187
    ```

## Problem 2:
``` shell
$ conda list
conda: command not found
```
* Solve:
    [Reference](https://stackoverflow.com/questions/18675907/how-to-run-conda)<br/>
    for anaconda 2 :
    ```shell
    export PATH=~/anaconda2/bin:$PATH
    ```
    for anaconda 3 :
    ```shell
    export PATH=~/anaconda3/bin:$PATH
    ```

## Problem 3:
“(base)” appear in front of my terminal prompt?

* Solve:
    [Reference](https://askubuntu.com/questions/1026383/why-does-base-appear-in-front-of-my-terminal-prompt)
    ```shell
    $ conda config --set auto_activate_base False
    ```

### Tips
```shell
$ gedit ~/.bashrc
```
[Reference](https://unix.stackexchange.com/questions/129143/what-is-the-purpose-of-bashrc-and-how-does-it-work)
This is a shell script that Bash runs. You can add the line bellow in this file
```shell
alias tmp='cd /tmp/'
```
Now, you can just enter in terminal
```shell
$ tmp
```
It will go to /tmp/ location. You can define any command you want, like:
```shell
alias m='make clean;make'
```
