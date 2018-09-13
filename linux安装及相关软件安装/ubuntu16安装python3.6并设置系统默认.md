# ubuntu16安装python3.6并设置系统默认

`sudo apt-get install software-properties-common`

`sudo add-apt-repository ppa:jonathonf/python-3.6 `
`sudo apt-get update `
`sudo apt-get install python3.6`

## 该系统默认设置

`cd /user/bin`

` rm python`

`ln -s python3.6m python`

## 升级pip

`python pip install -upgrade pip`

