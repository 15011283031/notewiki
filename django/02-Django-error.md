#### django 添加外键时出现异常
- 可以删除库内已经建设的表关联，然后重新添加
  1. 删除migrations下除0001外其他文件
  2. 删除数据库内所有通过model的表，注意app
  3. 重新migrations
  4. 重新migrate