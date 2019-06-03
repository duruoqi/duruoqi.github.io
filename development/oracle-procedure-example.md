## Oracle存储过程示例

> [首页](/index.html) / [数据库相关技术](/development/database.html)

```sql
-- 注意：
--   执行前，请先备份库表
--   执行用户：……
--   事务提交：每5000条提交一次

Declare
  Row_Num Number := 0;
Begin
  For c_Row in (
        SELECT 字段1, 字段2
          FROM 表1
         WHERE 筛选条件) Loop
    Update 表2 t
       Set t.字段1 = c_Row.字段1,
           t.字段2 = 字段2
     Where t.筛选字段 = c_Row.字段1;
    Row_Num := Row_Num + 1;
    If Mod(Row_Num, 5000) = 0 Then
      Commit;
    End If;
  End Loop 
  Commit;
End;
/
```
