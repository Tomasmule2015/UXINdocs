1.部署流程

- 代码下载，修改后上传

  ​       从 SVN下载代码，代码存放 172.16.3.190/svn/team/dev/server

  ​       cornerstone 配置 http server,  **Server:**172.16.3.190 **Name:** RexMa **Password:**vds8dj

- 切量部署 

  ​      编译环境： iTerm2  配置 172.16.3.142 , **Preference->Profiles**添加， General  **Name:** 172.16.3.142 , **Command:** expect ~/.ssh/ubuntu142 **Home directory:** /Users/Wuzhiren

  ​       ~/.ssh/ubuntu142 为本机文件，内容为：

        ``` u  
  #!/usr/bin/expect -f
    set user wuzhiren
    set host 172.16.3.142
    set password wuzhiren
    set timeout -1
  
    spawn ssh $user@$host
    expect "*assword:*"
    send "$password\r"
    interact
    expect eof
        ```

  ​        makefile位置为： ```/home/wuzhiren/workspace/server/applications/mps_video```

  ​        在mk.sh更改版本号，mk.sh -STEST=0  ,  0 , 1仅仅编译mps, 2 编译mps以及依赖的包

  ​        将编译好的包上传至```172.16.10.15/svn/uxin_svn/uxin_server/Release/mps```

  ​        用户名 rex.ma 密码 uxin@1234

  ​        发布系统每15分钟会扫描更新最新上传的包

  

  ​        登陆发布系统 <https://zbx.uxin001.com:4443/m>   用户名： uxin_ve    密码： uxin_ve

  ​        **应用部署->灰度部署** 进行切量更新， 最好在早上进行操作。查看记录是否更新成功。

  ​        

  ​      

- 服务在机器上的位置

  ​    在跳板机上mps所有

  ​    日志 /data/mps_live 

  

2.监测，性能指标

- 日志分析
- grafana监测
- 
- 

3.代码

- mp_main
- OSAL
- mps 与 mls, 以及其它外部交互
- mps数据流
- 

4.问题追踪

- 常见问题排查

     225.4 这台机器有问题？ 跟王海江