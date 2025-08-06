# 部署相关文档

本目录包含项目部署相关的配置文件和文档。

## 📁 文件说明

- `nginx.conf` - 完整的Nginx服务器配置文件（生产环境推荐）
- `nginx-simple.conf` - 简化版Nginx配置文件（快速部署）
- `deployment.md` - 详细的部署指南
- `docker/` - Docker相关配置（未来添加）

## 🚀 快速部署

### 选择配置文件

**简化版配置** - 适合快速部署和测试：
```bash
sudo cp nginx-simple.conf /etc/nginx/sites-available/my-ai-workshop
```

**完整版配置** - 适合生产环境，包含安全和性能优化：
```bash
sudo cp nginx.conf /etc/nginx/sites-available/my-ai-workshop
```

### Nginx部署步骤

1. 构建项目：`npm run build`
2. 复制配置文件（选择上面其中一个）
3. 启用站点：`sudo ln -s /etc/nginx/sites-available/my-ai-workshop /etc/nginx/sites-enabled/`
4. 测试配置：`sudo nginx -t`
5. 重启服务：`sudo systemctl restart nginx`

详细说明请参考 [deployment.md](./deployment.md)

## 📋 配置对比

| 特性 | 简化版 | 完整版 |
|------|--------|--------|
| Vue Router支持 | ✅ | ✅ |
| 静态资源缓存 | ✅ | ✅ |
| Gzip压缩 | 基础 | 完整 |
| 安全头设置 | ❌ | ✅ |
| SSL配置 | 基础 | 完整 |
| 性能优化 | 基础 | 完整 |
| 安全防护 | 基础 | 完整 |

## 🔧 配置自定义

在使用前请修改以下配置：

- `server_name` - 替换为您的域名
- `root` - 修改为实际的网站根目录路径
- SSL证书路径 - 如果启用HTTPS

## 📞 获取帮助

如遇到部署问题，请：

1. 查看 [deployment.md](./deployment.md) 详细文档
2. 检查Nginx错误日志：`sudo tail -f /var/log/nginx/error.log`
3. 提交Issue获取技术支持