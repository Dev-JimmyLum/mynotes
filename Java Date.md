### Java Date

```java
java.util.Date dt = new java.util.Date()   
java.text.SimpleDateFormat sdf = 
                new java.text.SimpleDateFormat("yyyy-MM-dd HH:mm:ss");

String currentTime = sdf.format(dt);
```

### Java Spring boot (mysql insert statement)

```java
jdbcTemplate.update(
    "INSERT INTO schema.tableName (column1, column2) VALUES (?, ?)",
    new Object[]{var1, var2}, new Object[]{Types.TYPE_OF_VAR1, Types.TYPE_OF_VAR2}
);




```






