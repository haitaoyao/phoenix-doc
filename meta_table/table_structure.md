
Phoenix Meta Table
---


name |type|descrition | 标记
---|---|---|--
 TABLE_SCHEM | varchar| 类似库名
TABLE_NAME|varchar|表名
COLUMN_NAME|varchar|列名 
TABLE_CAT|varchar
TABLE_TYPE|char
REMARKS|varchar|备注
DATA_TYPE|INTEGER| 数据类型，对应java.sql.Types， 在com.salesforce.phoenix.schema.PDataType 中使用
PK_NAME|varchar| | Y
TYPE_NAME |varchar|类型名称，类似VARCHAR这种
SELF_REFERENCING_COL_NAME | varchar| | Y 
REF_GENERATION|varchar| | Y 
TABLE_SEQ_NUM| BIGINT| 表序列号
COLUMN_COUNT|INTGER| 基本没有使用。 
SALT_BUCKETS|INTEGER|散列数。 类似shard份数
COLUMN_SIZE|INTEGER| column大小。 基本上只有INTEGER这种才会有值， varchar char等都是null
BUFFER_LENGTH|INTEGER| | Y 
DECIMAL_DIGITS|INTEGER|decimal类型digits位数
NUM_PREC_RADIX|INTEGER| | Y 
NULLABLE|INTEGER| 是否可以为空| Y 
COLUMN_DEF| varchar|  | Y
SQL_DATA_TYPE| INTEGER|sql数据类型, 但是基本没有地方使用 | Y 
SQL_DATETIME_SUB|INTEGER|  | Y 
CHAR_OCTET_LENGTH|INTEGER| | Y 
ORDINAL_POSITION|INTEGER|column顺序
IS_NULLABLE|VARCHAR| | Y 





