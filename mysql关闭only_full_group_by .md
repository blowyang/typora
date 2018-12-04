### 查看

`select @@sql_mode;`

### 关闭

```
SET sql_mode=(SELECT REPLACE(@@sql_mode, 'ONLY_FULL_GROUP_BY', ''));
```

