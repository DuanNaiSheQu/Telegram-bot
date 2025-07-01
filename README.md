# Telegram-bot
Telegram机器人源码平台，开源社区
# Telegram机器人源码开源平台

一个功能完整的Telegram机器人源码分享平台，支持文件上传、下载、付费购买、USDT支付等功能。

## 🚀 功能特性

### 核心功能
- **用户管理**: 用户注册、登录、个人资料管理
- **文件管理**: 文件上传、下载、分类、搜索
- **支付系统**: USDT支付、余额充值、交易记录
- **安全防护**: 文件病毒扫描、加密存储、访问控制
- **权限控制**: 用户权限管理、文件访问权限

### Telegram机器人功能
- **智能菜单**: Reply Keyboard + Inline Keyboard组合界面
- **文件操作**: 
  - 📤 上传文件 (支持最大5GB)
  - 📁 我的文件 (查看自己上传的文件)
  - 🔍 搜索文件 (搜索平台所有文件)
  - 💰 设置价格 (为文件设置自定义价格)
- **支付功能**:
  - 💳 余额充值 (USDT支付)
  - 📊 交易记录
  - 💰 余额查询
- **用户功能**:
  - 👤 个人资料
  - ⚙️ 设置选项
  - 📞 联系客服

### 技术特性
- **异步架构**: 基于asyncio的高性能异步处理
- **数据库支持**: SQLite/MySQL双数据库支持
- **文件安全**: 病毒扫描、文件加密、类型验证
- **区块链集成**: TRON网络USDT支付
- **API接口**: FastAPI RESTful API
- **日志监控**: 结构化日志、性能监控
- **Docker支持**: 容器化部署

## 📋 系统要求

- Python 3.8+
- SQLite 3.x 或 MySQL 5.7+
- Redis (可选，用于缓存)
- 至少2GB内存
- 10GB可用磁盘空间

## 🛠️ 安装部署

### 1. 克隆项目
```bash
git clone https://github.com/your-username/telegram-bot-platform.git
cd telegram-bot-platform
```

### 2. 创建虚拟环境
```bash
python -m venv venv
source venv/bin/activate  # Linux/Mac
# 或
venv\Scripts\activate  # Windows
```

### 3. 安装依赖
```bash
pip install -r requirements.txt
```

### 4. 配置环境变量
```bash
cp .env.example .env
# 编辑 .env 文件，填入你的配置信息
```

### 5. 初始化数据库
```bash
python -m alembic upgrade head
```

### 6. 启动服务
```bash
# 启动机器人
python main.py

# 或启动API服务器
uvicorn src.api.main:app --host 0.0.0.0 --port 8000
```

## ⚙️ 配置说明

### 必需配置
```env
# Telegram机器人Token (从@BotFather获取)
TELEGRAM_BOT_TOKEN=your_bot_token_here

# 数据库连接
DATABASE_URL=sqlite:///./bot_platform.db

# 安全密钥
SECRET_KEY=your_secret_key_here
ENCRYPTION_KEY=your_32_character_encryption_key
```

### 可选配置
```env
# USDT支付配置
TRON_API_KEY=your_tron_api_key
PLATFORM_USDT_ADDRESS=your_usdt_address

# 文件存储配置
MAX_FILE_SIZE=5368709120  # 5GB
UPLOAD_DIR=./uploads

# 安全设置
VIRUS_SCAN_ENABLED=true
FILE_ENCRYPTION_ENABLED=true
```

## 🏗️ 项目结构

```
telegram-bot-platform/
├── src/                    # 源代码目录
│   ├── bot/               # Telegram机器人模块
│   │   ├── handlers/      # 消息处理器
│   │   ├── keyboards/     # 键盘布局
│   │   └── telegram_bot.py
│   ├── models/            # 数据模型
│   │   ├── user.py       # 用户模型
│   │   ├── file.py       # 文件模型
│   │   └── ...
│   ├── database/          # 数据库模块
│   ├── utils/             # 工具函数
│   ├── api/              # API接口
│   └── config.py         # 配置管理
├── alembic/              # 数据库迁移
├── uploads/              # 文件上传目录
├── logs/                 # 日志目录
├── requirements.txt      # Python依赖
├── main.py              # 主程序入口
└── README.md            # 项目说明
```

## 🎯 使用指南

### 用户操作流程

1. **开始使用**
   - 发送 `/start` 命令启动机器人
   - 系统自动创建用户账户

2. **上传文件**
   - 点击 "📤 上传文件" 按钮
   - 发送文件给机器人
   - 设置文件价格和描述

3. **搜索下载**
   - 点击 "🔍 搜索文件" 按钮
   - 输入关键词搜索
   - 选择文件进行购买下载

4. **余额管理**
   - 点击 "💳 余额充值" 进行USDT充值
   - 查看 "📊 交易记录" 了解消费情况

### 管理员功能

- 用户管理：查看、编辑、禁用用户
- 文件管理：审核、删除、分类文件
- 财务管理：查看平台收入、提现管理
- 系统监控：查看系统状态、日志分析

## 🔒 安全特性

### 文件安全
- **病毒扫描**: 集成ClamAV病毒扫描引擎
- **文件加密**: AES-256加密存储敏感文件
- **类型验证**: 严格的文件类型和大小限制
- **访问控制**: 基于用户权限的文件访问控制

### 数据安全
- **数据加密**: 敏感数据字段加密存储
- **SQL注入防护**: 使用ORM防止SQL注入
- **XSS防护**: 输入数据过滤和转义
- **CSRF防护**: API接口CSRF令牌验证

### 支付安全
- **区块链验证**: TRON网络交易验证
- **双重确认**: 支付状态多重验证
- **风控系统**: 异常交易检测和拦截

## 📊 API文档

启动服务后访问 `http://localhost:8000/docs` 查看完整的API文档。

### 主要API端点

- `GET /api/v1/users/me` - 获取当前用户信息
- `POST /api/v1/files/upload` - 上传文件
- `GET /api/v1/files/search` - 搜索文件
- `POST /api/v1/payments/recharge` - 余额充值
- `GET /api/v1/transactions` - 交易记录

## 🐳 Docker部署

### 使用Docker Compose
```bash
# 构建并启动服务
docker-compose up -d

# 查看日志
docker-compose logs -f

# 停止服务
docker-compose down
```

### 单独使用Docker
```bash
# 构建镜像
docker build -t telegram-bot-platform .

# 运行容器
docker run -d \
  --name bot-platform \
  -p 8000:8000 \
  -v ./uploads:/app/uploads \
  -v ./logs:/app/logs \
  --env-file .env \
  telegram-bot-platform
```

## 🔧 开发指南

### 开发环境设置
```bash
# 安装开发依赖
pip install -r requirements-dev.txt

# 代码格式化
black src/
isort src/

# 类型检查
mypy src/

# 运行测试
pytest tests/
```

### 数据库迁移
```bash
# 创建新迁移
alembic revision --autogenerate -m "描述"

# 应用迁移
alembic upgrade head

# 回滚迁移
alembic downgrade -1
```

## 📈 性能优化

### 数据库优化
- 合理使用索引
- 查询优化和缓存
- 连接池配置

### 文件处理优化
- 异步文件上传
- 分块传输大文件
- 缓存热门文件

### 内存优化
- 对象池管理
- 垃圾回收优化
- 内存使用监控

## 🐛 故障排除

### 常见问题

1. **机器人无响应**
   - 检查Token是否正确
   - 确认网络连接正常
   - 查看日志错误信息

2. **文件上传失败**
   - 检查文件大小限制
   - 确认上传目录权限
   - 查看磁盘空间

3. **支付问题**
   - 验证USDT地址配置
   - 检查区块链网络状态
   - 确认API密钥有效

### 日志分析
```bash
# 查看实时日志
tail -f logs/bot.log

# 搜索错误日志
grep "ERROR" logs/bot.log

# 分析性能日志
grep "PERFORMANCE" logs/bot.log
```

## 🤝 贡献指南

1. Fork 项目
2. 创建功能分支 (`git checkout -b feature/AmazingFeature`)
3. 提交更改 (`git commit -m 'Add some AmazingFeature'`)
4. 推送到分支 (`git push origin feature/AmazingFeature`)
5. 开启 Pull Request

## 📄 许可证

本项目采用 MIT 许可证 - 查看 [LICENSE](LICENSE) 文件了解详情。

## 📞 支持与联系

- **问题反馈**: [GitHub Issues](https://github.com/your-username/telegram-bot-platform/issues)
- **功能建议**: [GitHub Discussions](https://github.com/your-username/telegram-bot-platform/discussions)
- **技术支持**: support@yourplatform.com
- **Telegram群组**: @your_support_group

## 🙏 致谢

感谢以下开源项目的支持：
- [python-telegram-bot](https://github.com/python-telegram-bot/python-telegram-bot)
- [FastAPI](https://github.com/tiangolo/fastapi)
- [SQLAlchemy](https://github.com/sqlalchemy/sqlalchemy)
- [Alembic](https://github.com/sqlalchemy/alembic)

---

⭐ 如果这个项目对你有帮助，请给它一个星标！
