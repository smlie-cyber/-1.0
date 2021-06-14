第1步：

cd /ql

第2步:

//如果你是amd64架构（服务器，PC等）
wget https://gitee.com/mujin2333/JDC/raw/master/linux_amd64.zip & unzip linux_amd64.zip
//如果你是arm架构（N1，路由器，树莓派等）
wget https://gitee.com/mujin2333/JDC/raw/master/linux_amd64.zip & unzip linux_arm.zip

第3步:

chmod 777 JDC
./JDC
这时会生成配置文件，再次运行会出现报错，我们需要修改配置文件。


第4步：

vi config.toml
#公告设置
[app]
    explain         = "扫码后请返回页面完成登录" #页面使用说明显示
    path            = "/ql/config/auth.json" #QL文件路径设置，一般无需更改
    QLip            = "http://127.0.0.1" #青龙面板的ip，部署于一台服务器时不用更改
    QLport          = "5700" #青龙面板的端口，默认为5700
    logName         = "chinnkarahoi_jd_scripts_jd_bean_change" #日志脚本名称
    allowAdd        = "0" #是否允许添加账号（0允许1不允许）不允许添加时则只允许已有账号登录

#web服务设置
[server]  address        = ":5701" #端口号设置
    serverRoot     = "public" #静态目录设置，请勿更改  serverAgent    = "JDCookie" #服务端UA

#模板设置
[viewer]  Delimiters  =  ["${", "}"] #模板标签，请勿更改

第5步：再次输入命令运行即可。

nohup ./JDC &

第6步：开放端口

firewall-cmd --zone=public --add-port=5701/tcp --permanent

然后访问网址：http://ip:5701 即可进入如下界面：
