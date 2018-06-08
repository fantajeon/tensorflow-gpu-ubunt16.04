

# NVIDIA Driver
```bashshell
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
Menu > System Settings > Software Update > Addtional Drivers
```
some tips: X window stop
```bashshell
sudo service lightdm stop    # Xorg stop
# install nvidia driver(you should get download driver install file and install it manually)
sudo service lightdm start   # Xorg start
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
set-window-option -g mode-keys vi

```

# VIM
```
sudo apt install vim
git clone https://github.com/gmarik/Vundle.vim.git ~/.vim/bundle/Vundle.vim
mkdir -p ~/.vim/autoload ~/.vim/bundle && curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim
```
```VIM
execute pathogen#infect()
set nocompatible
filetype off
" set the runtime path to include Vundle and initialize
set rtp+=~/.vim/bundle/Vundle.vim
call vundle#begin()
" let Vundle manage Vundle, required
Plugin 'VundleVim/Vundle.vim'
Plugin 'tpope/vim-fugitive'
Bundle 'nathanaelkane/vim-indent-guides'
Plugin 'https://github.com/tomasr/molokai.git'

" All of your Plugins must be added before the following line
call vundle#end()            " required
filetype plugin indent on    " required
" To ignore plugin indent changes, instead use:
"filetype plugin on
"
" Brief help
" :PluginList       - lists configured plugins
" :PluginInstall    - installs plugins; append `!` to update or just :PluginUpdate
" :PluginSearch foo - searches for foo; append `!` to refresh local cache
" :PluginClean      - confirms removal of unused plugins; append `!` to auto-approve removal
"
"
"
"

filetype plugin indent on
syntax on

set term=screen-256color
set cursorline
set modelines=0
set softtabstop=4
set tabstop=4
set shiftwidth=4
set expandtab
"colorscheme evening
set autoindent
set nobackup
set nowritebackup
set ignorecase
set noswapfile
" set list   "hide hidden character
set hlsearch
let python_highlight_all = 1
set shiftwidth=4
set showbreak=+++]
set linebreak
set wrap

" Indent Guide Lines
let g:indent_guides_enable_on_vim_startup = 1
let g:indent_guides_auto_colors = 0
let g:indent_guides_start_level=1
let g:indent_guides_guide_size=0
autocmd VimEnter,Colorscheme * :hi IndentGuidesOdd  guibg=#080808   ctermbg=232
autocmd VimEnter,Colorscheme * :hi IndentGuidesEven guibg=#121212 ctermbg=233

au BufRead,BufNewFile *.py,*.pyw set expandtab
au BufRead,BufNewFile *.py,*.pyw set shiftwidth=2
au BufRead,BufNewFile *.py,*.pyw set softtabstop=2
au BufRead,BufNewFile *.py,*.pyw set ts=2
au BufRead,BufNewFile *.py,*.pyw set sw=2 et
au BufRead,BufNewFile *.py,*.pyw set tabstop=2

au BufRead,BufNewFile *.c set noexpandtab
au BufRead,BufNewFile *.h set noexpandtab

" install molokai only by :PluginSearch in vim
colorscheme molokai
hi Visual term=reverse cterm=reverse guibg=Yellow
```

```bashshell
vim +PluginInstall +qall
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
```

# Micellious
```bashshell
pip install opencv-python
pip install tqdm
pip install better_exceptions
pip install gpustat
```
