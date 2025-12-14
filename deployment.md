Step1: 准备离线包
    
    1.拉取所需镜像
    docker pull requarks/wiki:2.5.308

    2.打包所有镜像为tar文件
    docker save requarks/wiki:2.5.308 -o "D:\工作\中芯工作\项目\智能值守\wiki.js\离线部署\wiki.tar"

    3.修改yml文件
        端口号

    4.将镜像上传至github或其他可在公司公共电脑下载的平台


Step2: 在离线电脑上部署label-studio
        1.在目标服务器上建立label studio文件夹
        mkdir -p /opt/label-studio
        2.加载 Docker 镜像
        docker load -i label-studio.tar
        3.验证是否成功
        docker images | grep label-studio
        4.启动服务
        docker compose up -d
        5.验证运行状态
        docker compose ps
        # 查看日志
        docker compose logs -f label-studio

