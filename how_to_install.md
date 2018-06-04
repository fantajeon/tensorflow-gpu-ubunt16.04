

# NVIDIA Driver
```bashshell
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
Menu > System Settings > Software Update > Addtional Drivers
```

# CUDA(9.0, not 9.1)
```bashshell
https://developer.nvidia.com/cuda-downloads
```
go to legacy release

# ~/.bashrc
```
export PATH=/usr/local/cuda/bin:${PATH}
export LD_LIBRARY_PATH=/usr/local/cuda/lib64:${LD_LIBRARY_PATH} 
```

# cuDNN(for 9.0)
https://developer.nvidia.com/cudnn
go to legacy release

# ldconfig
```
sudo ldconfig
```

# TWEAK(swap capslock and ctrl)
```
sudo apt install gnome-tweak-tool
```

# TMUX
```
sudo apt install tmux
vi ~/.tmux.conf
set -g prefix C-a
unbind C-b
bind-key C-a send-prefix
bind a send-prefix

set -g default-terminal "xterm-256color"
set -g history-limit 3000

```

# VIM
```
sudo apt install vim
git clone https://github.com/gmarik/Vundle.vim.git ~/.vim/bundle/Vundle.vim
mkdir -p ~/.vim/autoload ~/.vim/bundle && curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim
```

# PYTHON 3.6
```
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt-get update
sudo apt-get install python3.6 python3.6-dev virtualenv
```

# Build Virtual Env
```
virtualenv --system-site-packages -p python3.6 tf
source ~/tf/bin/activate
```

# Tensorflow-GPU install under (tf) virtualenv
```
easy_install -U pip
pip install --upgrade tensorflow-gpu
   or
pip install tf-nightly-gpu
   or 
pip install --upgrade https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow_gpu-1.8.0rc0-cp36-cp36m-linux_x86_64.whl
```

# tensorflow validation
```PYTHON
import tensorflow as tf
hello = tf.constant("Hello, TensorFlow!")
sess = tf.Session()
sess.run(hello)
```

# install pymssql
```
export PYMSSQL_BUILD_WITH_BUNDLED_FREETDS=1
pip install pymssql
```

# install extra packages
```
pip install pymysql
pip install dateutils
```
# REVERSE SSH(Gateway out of NAT)
```
# sudo apt install -y openssh-server
/home/deepuser> cat > reverse_ssh.sh
#!/bin/bash
ssh -f -nNT -o ServerAliveInterval=10 -o ExitOnForwardFailure=yes -o TCPKeepAlive=yes -R XXXXX:127.0.0.1:22 ubuntu@X5XXXXX -i ~/XXXXXX.pem
```
```
/home/deepuser> chmod +x reverse_ssh.sh
```
```
/home/deepuser> crontab -e
MAILTO=""
*/10 * * * * /home/xxxxx/reverse_ssh.sh
```
```
/home/deepuser> sudo service cron reload
```

# matplob
```bashshell
sudo apt install python3.6-tk
pip install matplotlib
```

# OpenGYM
```bashshell
sudo apt install -y swig cmake zlib1g-dev
git clone https://github.com/openai/gym.git
cd gym
pip install -e '.[all]'
