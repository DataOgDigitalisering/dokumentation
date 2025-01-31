# CHRU_HRKube

## Tabeller

<center>
<iframe width="900" height="600" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={01f418ad-55f1-4891-b33a-51c44c26a2f7}&action=embedview&wdAllowInteractivity=False&Item=sql_tables&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
<br>


## Relationer
<center>
<iframe width="900" height="600" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={01f418ad-55f1-4891-b33a-51c44c26a2f7}&action=embedview&wdAllowInteractivity=False&Item=dmv_relationships&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
<br>



## Measures
<center>
<iframe width="900" height="600" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={01f418ad-55f1-4891-b33a-51c44c26a2f7}&action=embedview&wdAllowInteractivity=False&Item=dmv_measures&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
<br>



## Dependencies

{::options parse_block_html="true" /}
<details><summary markdown="span">Measure-til-measure</summary>
Measures (dependent) med én eller flere afhængigheder af andre measures (reference).
<center>
<iframe width="900" height="600" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={01f418ad-55f1-4891-b33a-51c44c26a2f7}&action=embedview&wdAllowInteractivity=False&Item=dmv_dep_m2m&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
</details>
{::options parse_block_html="false" /}
<br>

{::options parse_block_html="true" /}
<details><summary markdown="span">Measure-til-measure (etiketter og farver)</summary>
Measures (dependent) med én eller flere afhængigheder af andre measures (reference).
<center>
<iframe width="900" height="600" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={01f418ad-55f1-4891-b33a-51c44c26a2f7}&action=embedview&wdAllowInteractivity=False&Item=dmv_dep_m2m_rest&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
</details>
{::options parse_block_html="false" /}
<br>

{::options parse_block_html="true" /}
<details><summary markdown="span">Table-til-measure</summary>
Measures (dependent) med én eller flere afhængigheder af tabel-kolonner (refence).
<center>
<iframe width="900" height="600" frameborder="0" scrolling="no" src="https://regionh-my.sharepoint.com/personal/tanja_olsen_la_cour_regionh_dk/_layouts/15/Doc.aspx?sourcedoc={01f418ad-55f1-4891-b33a-51c44c26a2f7}&action=embedview&wdAllowInteractivity=False&Item=dmv_dep_t2m&wdHideGridlines=True&wdInConfigurator=True&wdInConfigurator=True"></iframe>
</center>
</details>
{::options parse_block_html="false" /}
<br>



# Metadata

<!-- TABELLER -->
{::options parse_block_html="true" /}
<details><summary markdown="span">Tabeller: SQL-query til træk af metadata om tabeller i SSMS</summary>
```sql
USE [Flis2_LønHR_v2];

SELECT
   col.TABLE_SCHEMA AS 'Skema'
   ,col.TABLE_NAME AS 'Tabel'
   ,col.ORDINAL_POSITION as ' '
   ,COALESCE(LEFT(keys.CONSTRAINT_NAME,1), NULL) AS '_Key'
   ,col.COLUMN_NAME AS 'Kolonne'
   ,DATA_TYPE AS 'Type'
   --,CHARACTER_MAXIMUM_LENGTH AS 'CharMaxLength'
   --,NUMERIC_PRECISION AS 'NumPrec'
   --,DATETIME_PRECISION AS 'dtPrec'
   ,COALESCE(DATETIME_PRECISION, NUMERIC_PRECISION, CHARACTER_MAXIMUM_LENGTH, NULL ) AS 'Len/Prec'
   ,CASE WHEN IS_NULLABLE = 'YES' THEN 'Y' ELSE 'N' END AS 'NULLs'
   ,COALESCE(colDesc.columnDescription, NULL) AS '_Beskrivelse'
  FROM INFORMATION_SCHEMA.COLUMNS col
INNER JOIN information_schema.TABLES tbl 
   ON col.table_name = tbl.table_name
LEFT JOIN INFORMATION_SCHEMA.KEY_COLUMN_USAGE keys ON 1=1
   AND keys.TABLE_SCHEMA = col.TABLE_SCHEMA
   AND keys.TABLE_NAME = col.TABLE_NAME
   AND keys.COLUMN_NAME = col.COLUMN_NAME			
LEFT JOIN (
	SELECT 
		sc.object_id
		,sc.column_id
		,sc.name
		,colProp.[value] AS 'ColumnDescription'
      FROM sys.columns sc
	INNER JOIN sys.extended_properties colProp ON 1=1
		AND colProp.major_id = sc.object_id
        AND colProp.minor_id = sc.column_id
        AND colProp.name = 'MS_Description' 
   ) colDesc
   ON 1=1 
   AND colDesc.object_id = object_id(tbl.table_schema + '.' + tbl.table_name)
   AND colDesc.name = col.COLUMN_NAME
WHERE 1=1
   AND col.TABLE_SCHEMA in ('chru_cube', 'DM_FL_HR')
ORDER BY Skema asc, Tabel ASC, ' ' ASC  
```
</details>
<br/>
{::options parse_block_html="false" /}



{::options parse_block_html="true" /}
<!-- MEASURES -->
<details><summary markdown="span">Measures: DMV-query til træk af metadata om measures i DaxStudio</summary>
```sql
SELECT
	[DisplayFolder] AS [Mappe]
	,[Name] AS [Measure]
	--,[DataType] AS [Type]
	,[FormatString] AS [Format]
	,[Expression] AS [DAX]
	,[Description] AS [Beskrivelse]
	,[ModifiedTime] AS [Redigeret]
  FROM $SYSTEM.TMSCHEMA_MEASURES
ORDER BY [Name]
```
</details>
<br>
{::options parse_block_html="false" /}
