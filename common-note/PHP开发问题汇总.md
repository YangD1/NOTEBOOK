# 开发中遇到的问题汇总
### 阿里云邮件推送使用 SMTP 发送邮件，线上站点使用https后无法正常推送？
SMTP端口号: 80，25，465（SSL加密）
更换端口为80即可

### Laravel 5.1 使用 MySQL 7 数据库遇到 Invalid default value for 'created_at'

服务器升级 MySQL 5.7 下，老项目 Laravel 5.1 的数据库表结构修改时会遇到：
```
Invalid default value for 'created_at'
```
那是因为 MySQL 5.7 在 strict 模式开启时，不允许 0000-00-00 作为 timestamp 的默认值，而在 Laravel 5.3 以下，默认 strict 是开启的。

在新创建的 Migration 中，使用：
```
$table->nullableTimestamps()
```
来替代之前的 `timestamps()`。单独的时间字段使用：
```
$table->->timestamp()->useCurrent();
```
或者：
```
$table->->timestamp('xxx')->nullable();
```
对于已经存在的数据库，可以使用以下 SQL 直接修正（注意把 users 改为你的数据库表）：
```
ALTER TABLE `users` 
    CHANGE created_at created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL,
    CHANGE updated_at updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP NOT NULL;
```