# Python用户认证系统

这是一个基于Flask的用户认证系统，提供用户注册和登录API接口。

## 功能特点

- 用户注册
- 用户登录
- 密码加密存储
- RESTful API接口

## 系统要求

- Python 3.6+
- MariaDB数据库

## 安装步骤

1. 克隆项目到本地或服务器

2. 安装依赖包：
```bash
pip install -r requirements.txt
```

3. 配置MariaDB数据库
- 创建数据库：
```sql
CREATE DATABASE auth_db;
```
- 修改`app.py`中的数据库连接配置：
```python
app.config['SQLALCHEMY_DATABASE_URI'] = 'mysql+pymysql://用户名:密码@localhost/auth_db'
```

## 部署到腾讯云

1. 在腾讯云服务器上安装Python和MariaDB

2. 上传项目文件到服务器

3. 安装和配置Gunicorn：
```bash
gunicorn -w 4 -b 0.0.0.0:5000 app:app
```

## API接口说明

### 注册接口

- URL: `/api/register`
- 方法: POST
- 请求体:
```json
{
    "username": "用户名",
    "password": "密码"
}
```
- 响应示例：
```json
{
    "message": "注册成功"
}
```

### 登录接口

- URL: `/api/login`
- 方法: POST
- 请求体:
```json
{
    "username": "用户名",
    "password": "密码"
}
```
- 响应示例：
```json
{
    "message": "登录成功"
}
```

## 安全说明

- 密码使用SHA256加密存储
- 所有API响应都包含适当的HTTP状态码
- 实现了基本的错误处理机制
