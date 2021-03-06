
Phoenix Meta Table
---
## SYSTEM.TABLE

name | type | descrition | 标记
---|---|---|-----
TABLE_SCHEM | VARCHAR | 类似库名 | 
TABLE_NAME|VARCHAR|表名|
COLUMN_NAME|VARCHAR|列名 |
TABLE_CAT|VARCHAR| ——|
--上面的 都是主键column||---从在这里往下是非主键  |
TABLE_TYPE|char| ——|
REMARKS|VARCHAR|备注|
DATA_TYPE|INTEGER| 数据类型，对应java.sql.Types， 在com.salesforce.phoenix.schema.PDataType 中使用|
PK_NAME|VARCHAR| ——| Y
TYPE_NAME |VARCHAR|类型名称，类似VARCHAR这种|
SELF_REFERENCING_COL_NAME | VARCHAR| | Y 
REF_GENERATION|VARCHAR| ——| Y 
TABLE_SEQ_NUM| BIGINT| 表序列号
COLUMN_COUNT|INTGER| 基本没有使用。 
SALT_BUCKETS|INTEGER|散列数。 类似shard份数
COLUMN_SIZE|INTEGER| column大小。 基本上只有INTEGER这种才会有值， VARCHAR char等都是null |
BUFFER_LENGTH|INTEGER| | Y 
DECIMAL_DIGITS|INTEGER|decimal类型digits位数
NUM_PREC_RADIX|INTEGER| | Y 
NULLABLE|INTEGER| 是否可以为空| Y 
COLUMN_DEF| VARCHAR|  | Y
SQL_DATA_TYPE| INTEGER|sql数据类型, 但是基本没有地方使用 | Y 
SQL_DATETIME_SUB|INTEGER|  | Y 
CHAR_OCTET_LENGTH|INTEGER| | Y 
ORDINAL_POSITION|INTEGER|column顺序
IS_NULLABLE|VARCHAR| | Y 
SCOPE_CATALOG|VARCHAR| | Y
SCOPE_SCHEMA|VARCHAR| | Y
SCOPE_TABLE|VARCHAR| | Y
SOURCE_DATA_TYPE|INTEGER| | Y
IS_AUTOINCREMENT|INTEGER| | Y
COLUMN_MODIFIER|VARCHAR| | Y
DATA_TABLE_NAME| VARCHAR | | Y
INDEX_STATE| VARCHAR | |Y
IMMUTABLE_ROWS| VARCHAR| | Y

### 备注
* column_name 为null 时, 说明是表; column_name 不为空时, 代表表的column信息


## create table flow
flow chart for create table, [here](create_table_flow.png )
![Alt Text](create_table_flow.png)

* table flow code [websequencegram](https://www.websequencediagrams.com/)

```

title phoenix create table flow

PhoenixConnection -> PhoenixPreparedStatement :  new instance
PhoenixPreparedStatement -> PhoenixStatementParser : nextStatement start to parse statement
PhoenixStatementParser -> SQLParser : nextStatement
SQLParser -> PhoenixSQLParser : nextStatement
PhoenixSQLParser -> antlr : parse statement
antlr  -> ExecutableNodeFactory : createTable 
ExecutableNodeFactory --> -PhoenixConnection : return new ExecutableCreateTableStatement
PhoenixConnection -> ExecutableCreateTableStatement :  execute
ExecutableCreateTableStatement -> ExecutableCreateTableStatement : executeUpdate
ExecutableCreateTableStatement -> ExecutableCreateTableStatement : optimizePlan
ExecutableCreateTableStatement -> ExecutableCreateTableStatement : compilePlan
ExecutableCreateTableStatement -> CreateTableCompiler : compile
CreateTableCompiler --> -ExecutableCreateTableStatement : MutationPlan
ExecutableCreateTableStatement -> MutationPlan : execute
MutationPlan -> MetaDataClient : createTable

```



