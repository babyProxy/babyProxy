## ✨  BabyProxy ✨  · 以太坊抽水、转发矿池，一键搭建私人矿池

![minerProxy.PNGZz](https://bcn.135editor.com/files/users/1169/11697638/202203/Og7B9gZC_M93k.jpg "参数说明.jpg" )

- ✔ 新代码库迁移到这里， 旧代码库已删除：rgerd/babyProxy
- ⚡ 用于鱼池、币印、E池等以太坊/比特币矿池代理、中转、转发、抽水
- 🔭 请谨慎使用其他人的加料代码，懂的都懂

### Linux服务器部署教程

1、准备好你的linux服务器
- 推荐配置：Centos 7.x
- 区域：香港（大部分矿池CN已经被污染DNS，CN大陆服务器无法解析、访问）

2、执行(按顺序执行代码)：

#### 👆第一步：配置服务器环境, 依次执行以下命令，增加服务器连接数：
- 直接一行一行复制粘贴执行即可
```nashorn js
echo "root soft nofile 102400" >>/etc/security/limits.conf
echo "root hard nofile 102400" >>/etc/security/limits.conf
echo "DefaultLimitNOFILE=102400" >>/etc/systemd/system.conf
echo "DefaultLimitNPROC=102400" >>/etc/systemd/system.conf
echo "DefaultLimitNOFILE=102400" >>/etc/systemd/user.conf
echo "DefaultLimitNPROC=102400" >>/etc/systemd/user.conf

```

### ✌第二步：克隆仓库代码
```bash
# 克隆代码到本地
git clone https://github.com/babyProxy/babyProxy.git
# 进入项目目录
cd babyProxy
# 赋予执行权限
chmod +x babyProxy
```
至此，代码+服务器准备完毕，可以开始愉快地挖矿了。

### 👌第三步：根据需要转发的矿池，开启babyProxy矿池转发

#### 用法1️⃣ web网页配置（适合小白）
- 更新的你配置文件
  ```bash
    
    host: 0.0.0.0 # 你的服务器ip
    port: 9999 # 你的管理面板端口，登录web
    token: 123456 # 这个是你的网页登录口令，使用前请先修改
    webserver: true
    server:
      - port: "5555" # 你的服务器需要开放的端口，矿机连接这个端口
        ssl: 1 # 是否开启ssl加密，可选0 -> tcp 1 -> ssl
        proxypool: ssl://asia2.ethermine.org:5555 # 转发目标矿池
        devfee: 1 # 抽1%
        devpool: ssl://asia2.ethermine.org:5555 # 抽水矿池
        addr: 0x4d2755c4FFFF163a7637acd1388D547B894157B2 # 你的抽水钱包地址
        worker: devfee101 # 矿工名（随意填）
        reconnect: 20
        clientnum: 1000 # 最大连接客户端数
  
  ```
- session运行：
  ```bash
  chmod +x babyProxy_web
  bash ./babyProxy_web
  ```
- 后台持久化运行：
  ```bash
  nohup ./babyProxy_web &
  ```
![运行.png](/runlog.png "运行.jpg" )
- 执行命令后，浏览器打开端口：9999
![dashboard.png](/example_dash.png "dashboard.jpg" )

- 最后， 你的矿机配置：矿池api: 
- 格式： 你的服务器ip:你开启的转发端口
- 例如： 47.115.222.555:5555


#### 用法2️⃣ linux手动配置（适合熟悉linux的朋友）
- 已经提前为大家准备好了模板，替换为自己的钱包地址即可
- 参数说明

![参数说明.png](https://bcn.135editor.com/files/users/1169/11697638/202203/6jLBrL4c_JgJv.png "参数说明.jpg" )

- 鱼池：f2pool-6688.sh
- 币印：poolin-1883.sh
- E池： ethermine-14444.sh

❗ 需要转发哪个矿池执行以下命令即可：
```bash
nohup f2pool-6688.sh &
nohup poolin-1883.sh &
nohup ethermine-14444.sh &
```
#### 用法三3️⃣ 使用windows服务器
- 开放配置文件的服务器端口
- 双击执行：babyProxy_windows.exe
- 连接矿池挖矿

### 特别注意事项

❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗

- 矿池转发服务请务必记得开放对应的端口， 例如鱼池开放6688，币印开放1883等
- 1、在服务器 云服务商控制台 操作安全组，放行对应的端口，百度教程
- 2、在linux本机设置开放端口，centos、ubuntu等不同服务器开放方法不一，百度教程

❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗❗

#### 最后
- 💬 有疑问可以直接邮件咨询
- 📫 邮箱：588@usd.dog
- 😄 请我喝奶茶:
  - BTC：34URScr9mwe6SJUNDRx71iGCDjjt74aYhi
  - ETH：0x4d2755c4FFFF163a7637acd1388D547B894157B2
  - Gitcoin：0x4d2755c4FFFF163a7637acd1388D547B894157B2

