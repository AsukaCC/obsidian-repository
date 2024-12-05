#  pm2  
 PM2 是一个流行的 Node.js 进程管理工具，旨在帮助你管理和保持应用程序持续运行。它提供了多种功能来简化应用程序的部署和维护  

## 安装
```markdown
sudo npm install -g pm2
```

## 启动
```markdown
pm2 start </path/to/your/app.js> --name <my-node-app>
```

## 查看当前运行
```markdown
pm2 list
```

## 重启
```markdown
pm2 restart <my-node-app>
```

## 删除
```markdown
pm2 delete <my-node-app>
```

##  设置 PM2 开机自启动  
###  生成启动脚本  
```markdown
pm2 startup systemd

# 复制生成的脚本执行
# EX 
sudo env PATH=$PATH:/usr/bin pm2 startup systemd -u <your-username >--hp </home/your-username>
```

### 保存当前进程
```markdown
pm2 save
```

### 启动服务
```markdown
sudo systemctl start <pm2-your-username>
sudo systemctl enable <pm2-your-username>
```

