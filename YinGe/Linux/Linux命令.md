        ifconfig    # 查询网卡信息
        ifconfig eth0 192.168.118.2     # 分配192.168.118.2这个网络IP
        df      # 查看分区
# 文件处理命令
        ls                      # 显示所有文件，不包括隐藏文件
        ls -a                   # 显示所有文件，包括隐藏文件
        ls -l                   # 详细信息显示
        ls -d                   # 查看目录属性
        ls -h                   # 以合适的单位显示文件大小
        ls -i                   # 查看文件的inode号（inode存储文件的详细信息）
        mkdir [目录]            # 创建新目录
        mkdir -p                # 递归创建
        cd [目录]               # 切换目录
        cd ..                   # 回到上一级目录
        pwd                     # 显示当前所在的目录
        rmdir [目录]             # 删除空目录
        cp -rp [原文件或目录][目标目录] # 复制文件或目录
        cp -r                   # 复制目录（复制文件可以不用）
        cp -p                   # 保留文件属性
        mv                      # 剪切和改名
        rm -rf [文件或目录]     # 删除文件或目录(rm -rf *命令是删除当前目录下的所有文件)
        rm -r                   # 删除目录
        rm -f                   # 强制执行
        touch                   # 创建文件
        cat [文件名]            # 显示文件内容
        cat -n                  # 显示行号
        tac                     # 反过来显示文件内容
        more [文件名]           # 分页显示文件内容（不能回翻）
                ·（空格）或f    # 翻页
                ·（Enter）      # 换行
                ·q或Q           # 退出
        less [文件名]           # 分页显示文件内容（可向上翻页）
                ·（上箭头）     # 上翻一行
                ·pgup           # 上翻一页
                ·（/[关键字]）    #搜索关键字
                        ·n      # 下一个关键字
        head -n [行号] [文件名]  # 显示文件前几行
        tail -n [行号] [文件名]  # 显示文件后几行
        tail -f [文件名]        # 动态显示文件末尾内容
        ln -s [原文件] [目标文件]       # 创建软链接（快捷方式）
        ln [原文件] [目标文件]          # 创建硬链接（可以同步更新）
# 权限管理命令 
        chmod [{ugoa}{+-=}{rwx}] [文件或目录]   # 改变文件或目录权限（u是所有者，g是所属组，o是其他人，a是全部人，r是读，w是写，x是执行）
        chmod [XXX] [文件或目录]   # 改变文件或目录权限(r=4,w=2,x=1,rwx=7,rw=6,rx=5,wx=3)
        chmod -R        # 递归修改（改变目录权限的同时改变目录下所有文件的权限）
        chown [用户] [文件或目录]       # 改变文件或目录的所有者
        chgrp [用户组] [文件或目录]     # 改变文件或目录的所属组
# 文件搜索命令
        find [搜索范围(某个目录)] [匹配条件]      # 文件搜索 （[匹配条件]:例：-name init 只搜索范围内的init文件
                                                                           -name *init* 搜索范围内文件名中有init的文件
                                                                           -name init* 搜索范围内以init开头的文件
                                                                           -name init??? 搜索范围内以init开头后面接3个字母的文件
                                                                           -iname [文件名] 不区分大小写搜索
                                                                           -size [+n/-n/n(n为文件大小)] +n是查大于n的文件和目录，-n是查小于n的文件和目录，n是查等于n的文件和目录
                                                                           -user [用户名] 根据所有者查找
                                                                           -group [所属组] 根据所属组查找
                                                                           -cmin [+n/-n/n(n为时间)] +n是查被修改过文件属性大于n分钟的文件和目录，-n是查被修改过文件属性小于n分钟的文件和目录，n是查被修改过文件属性等于n分钟的文件和目录
                                                                           -amin [+n/-n/n(n为时间)] +n是查被访问时间大于n分钟的文件和目录，-n是查被访问时间小于n分钟的文件和目录，n是查被访问时间等于n分钟的文件和目录
                                                                           -mmin [+n/-n/n(n为时间)] +n是查被修改过文件内容大于n分钟的文件和目录，-n是查被修改过文件内容小于n分钟的文件和目录，n是查等于被修改过文件内容等于n分钟的文件和目录
                                                                           -type [f(文件)/d(目录)/l(软链接文件)] 根据文件类型查找
                                                                           -exec/-ok（-ok执行每一条语句时会询问） [命令] {} \;({} \;是固定搭配) 对搜索结果执行操作
                                                                           -inum [i节点] 根据i节点查找）
        find的特殊命令（可插入到find的匹配条件中）：-a 两个条件同时满足
                                                  -o 两个条件满足任意一个即可
        locat [文件名]          # 在文件资料库中查找文件
        updatedb        # 升级（更新）文件资料库
        locat -i        # 不区分大小写查找
        which [命令]    # 搜索命令所在目录及别名信息
        whereis [命令]  # 搜索命令所在目录及帮助文档路径
        grep            # 在文件中搜索字串匹配的行并输出
        grep -i         # 不区分大小写
        grep -v [指定字串][文件]        # 排除指定字串
        man/info [命令或配置文件（不需要写绝对路径）]    # 获得帮助信息（跟more的使用方法一样）
        whatid [命令]   # 查看命令简短信息
        apropos [配置文件]      # 查看配置文件的简短信息
        [命令] --help   # 查看这个命令可用的主要选项
        help [Shell内置命令]    # 获得Shell内置命令的帮助信息（man找不到的命令都是Shell命令）
        useradd [用户名]        # 添加新用户 
        passwd [用户名]         # 设置用户密码 
        who                   # 查看登录用户信息(w用来查看详细的信息) 
        uptime                  # Linux连续运行的时间 
        gzip [文件]             # 压缩文件(不能压缩目录，且压缩完后不保留原文件)
        gunzip/(gzip -d) [压缩文件]     # 解压缩文件 
        bzip2 -k [文件]         # 产生压缩文件后保留原文件
        bunzip2 [压缩文件]      # 解压缩
        bunzip2 -k [压缩文件]   # 解压缩后保留压缩包
        tar -zcfv [文件/目录]           # 打包、压缩目录(-c 打包，-z 压缩，-f 指定目录，-v 显示详细信息)
        tar -zxfv [文件/目录]           # 打包、压缩目录(-x 解包，-z 压缩，-f 指定目录，-v 显示详细信息) 
        zip [压缩后的文件名] [要压缩的文件]     # 压缩文件（能保留原文件）
        zip -r [压缩后的文件名] [要压缩的文件目录]     # 压缩文件目录（能保留原文件目录） 
        unzip [压缩文件名]              # 解压缩文件 
# 网络命令 
        write [用户名]  # 给在线用户发信息，以Ctrl+D保存结束，Delete键写错删除 
        wall [要发的信息]       # 给所有在线用户发信息，包括自己 
        ping -c [次数] IP地址        # 测试网络联通性（-c是指定发送次数） 
        ifconfig        # 查看网卡信息
        ifconfig [网卡名称] IP地址      # 查看和设置网卡信息
        mail [用户名]   # 发送电子邮件 
        mail    # 查看邮件 
        last    # 列出目前与过去登录系统的用户信息 
        lastlog         # 检查某特定用户上次登录的时间 
        lastlog -u [用户id]     # 检查某单个用户上次登录的时间 
        traceroute [网址]     # 显示数据包到主机间的路径 
        netstat [选项]          # 显示网络相关信息（常用选项:-t：TCP协议
                          -u：UDP协议
                          -l：监听
                          -r：路由
                          -n：显示IP地址和端口号） 
        setup   # 配置网络 
        moubt /dev/sr0(设备文件名) /mnt/cdrom(挂载点)   # 挂载