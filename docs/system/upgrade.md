# 升级文档

!!! warning "更新前请一定要做好备份工作"

### 升级步骤
=== "一键升级"
    !!! tip ""
        ```sh
        # 如果已经部署旧版本，可通过如下命令一键升级至最新版本:
        cd /opt/hummerrisk-installer-v0.1.0  # v0.1.0 是版本号, 你的环境可能是其他的版本, 修改成对应的即可
        # 如果使用离线版本: cd /opt/hummerrisk-offline-installer-v0.1.0

        hrctl upgrade
        ```

=== "在线升级"
    !!! tip ""
        ```sh
        cd /opt
        wget https://github.com/HummerRisk/installer/releases/download/{{ hummerrisk.version }}/hummerrisk-installer-{{ hummerrisk.version }}.tar.gz
        tar -xf hummerrisk-installer-{{ hummerrisk.version }}.tar.gz
        cd hummerrisk-installer-{{ hummerrisk.version }}
        ```
        ```sh
        hrctl upgrade v0.2.0
        ```
        ```nginx hl_lines="1 35"
        是否将版本更新至 {{ hummerrisk.version }} ? (y/n)  (默认为 n): y

        1. 升级镜像文件
        Docker: Pulling from mysql:5.7.34 	        [ OK ]
        Docker: Pulling from hummerrisk:{{ hummerrisk.version }} 	    [ OK ]
        完成

        2. 备份数据库
        正在备份...
        mysqldump: [Warning] Using a password on the command line interface can be insecure.
        [SUCCESS] 备份成功! 备份文件已存放至: /opt/hummerrisk/db_backup/hummerrisk-2022-07-01_08:30:30.sql

        3. 清理镜像
        是否需要清理旧版本镜像文件? (y/n)  (默认为 n): y
        Untagged: hummerrisk:v0.1.0

        4. 升级成功, 可以重启程序了
        cd /opt/hummerrisk-installer-{{ hummerrisk.version }}
        hrctl restart
        ```
        ```sh
        hrctl down
        hrctl start
        ```

=== "离线升级"

    !!! tip ""
        ```sh
        cd /opt
        tar zxf hummerrisk-offline-installer-{{ hummerrisk.version }}.tar.gz
        cd hummerrisk-offline-installer-{{ hummerrisk.version }}
        ```
        ```sh
        hrctl upgrade
        ```
        ```nginx hl_lines="1 35"
        是否将版本更新至 {{ hummerrisk.version }} ? (y/n)  (默认为 n): y

        1. 升级镜像文件
        Docker: Pulling from mysql:5.7.34 	        [ OK ]
        Docker: Pulling from hummerrisk:{{ hummerrisk.version }} 	    [ OK ]
        完成

        2. 备份数据库
        正在备份...
        mysqldump: [Warning] Using a password on the command line interface can be insecure.
        [SUCCESS] 备份成功! 备份文件已存放至: /opt/hummerrisk/db_backup/hummerrisk-2022-07-19_20:30:30.sql

        3. 清理镜像
        是否需要清理旧版本镜像文件? (y/n)  (默认为 n): y
        Untagged: hummerrisk:v0.1.0

        4. 升级成功, 可以重启程序了
        cd /opt/hummerrisk-offline-installer-{{ hummerrisk.version }}
        hrctl restart
        ```
        ```sh
        hrctl down
        hrctl start
        ```

!!! warning "默认 web 登录账户: admin 密码：hummer"
