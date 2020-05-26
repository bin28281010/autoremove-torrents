# autoremove-torrents
configuration of autoremove-torrents
 
# 配置

**配置文件路径**

`/root/.config/autoremove/config.yml`

**配合crontab使用**

`* */6 * * * autoremove-torrents --conf=/root/.config/autoremove/config.yml --log=/root/.config/autoremove/logs`

--logs参数指定的文件路径一定要是提前存在的。

**手动运行**

`autoremove-torrents --conf=/root/.config/autoremove/config.yml --log=/root/.config/autoremove/logs`

**配置示例**

```
# 一个任务块
my_task: # 第一部分：任务名称
  # 第二部分：登录信息
  client: qtortorrent
  host: http://127.0.0.1:9091
  username: admin
  password: adminadmin
  # 第三部分：策略块（删除条件）
  strategies:
    strategy1: # 第1部分：策略名称
      # 第2部分：过滤器
      categories:
        - IPT
      # 第3部分：删除条件
      ratio: 1
      seeding_time: 1209600
    strategy2:
      all_categories: true
      excluded_categories:
        - IPT
      seeding_time: 259200
    # 这里可以添加更多策略
  # 第四部分：决定是否同时删除数据（可选项）
  delete_data: true

# 这里可以添加更多任务
```
配置参数参考: https://autoremove-torrents.readthedocs.io/zh_CN/latest/inst.html
