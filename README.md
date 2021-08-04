# pyspark-utils
Some util Pyspark functions for Data transformation

Utils: General Shared Functions <BR>
** Description: Notebook created to deliver some common use Functions in Databricks to make our lives easier.<BR><BR>
___
> ** FUNCTION: createTableFromDF(dfUtil,database,tableName,area,subject,dropTable,writeMode): ** <BR>
Used to Create a Delta Table from a Spark Dataframe in one of the existing Databases in a dynamic way.
The Table Schema has to be already defined in the parameter DataFrame so the Table's Columns are created with the appropriate data formats.
>>** Parameters Needed: **
 * **dfUtil:** (Spark DF) The Dataframe containing the data that you want to create the Delta Table.
 * **database:** (String) use the 'sandbox' value to include the table in the sandbox database.
 * **tableName:** (String) the name of the Table you want to create in Databricks.
 * **area:** (String) the name of your area in the Sandbox (egs: 'credit-risk','data-engineers','data-scientists').
 * **subject:** (String) the subject/project/username that you are creating this table for. Can be you username in the Sandbox
 * **dropTable:** (Boolean) if you want to Drop the table from the database before creating it. (eg: True/False)
 * **writeMode:** (String) The write mode for you to record the data in the table. (eg: 'append': always appends the data in the table / 'overwrite': always overwrites the data in the table.)
  
>>** Example Code: ** <BR>
 createTableFromDF( dftst , 'sandbox' , 'test_table_name' , 'data-engineers' , 'fimazu' , False , 'append' ) <BR>

> ** <br> FUNCTION: moveFileFromDBFSToSandbox(area,sourceFile,targetFile): ** <BR>
Used to move files uploaded manually into Databricks DBFS to the target area Sandbox. <BR>
  
>>** Parameters Needed: **
 * **area:** (String) the name of your area in the Sandbox (egs: 'credit-risk','data-engineers','data-scientists').
 * **sourceFile:** (String) the name of the source file uploaded into DBFS.
 * **targetFile:** (String) the name of target file to be copied to the area Sandbox. the file can be renamed.
  
>>** Example Code: ** <BR>
 moveFileFromDBFSToSandbox('data-engineers','testSourceFile.csv','testDestinationFile.csv'):

> ** <br> FUNCTION: flatten_structs(nested_df): ** <BR>
Used to flatten nested structured columns in a Dataframe (eg: Struct type columns). Just pass the dataframe containing the Nested Columns as parameter. <BR>
  
>>** Parameters Needed: **
 * **Nested Data Frame (df):** The Dataframe containing the desired columns that you need un-nested. A new Dataframe will be returned.
  
>>** Example Code: ** <BR>
 df_Final = flatten_structs( df_StructColumns )  
  
> ** <br> FUNCTION: flatten_array_struct_df(nested_df): ** <BR>
Used to flatten nested columns in a Dataframe (eg: Array type columns). Just pass the dataframe containing the Nested Columns as parameter. <BR>
  
>>** Parameters Needed: **
 * **Nested Data Frame (df):** The Dataframe containing the desired columns that you want need un-nested. A new Dataframe will be returned.
  
>>** Example Code: ** <BR>
 df_Final = flatten_array_struct_df( df_NestedColumns )

> ** <br> FUNCTION: parseJSONColumns(nested_df): ** <BR>
Used to deserialize Json Columns that are in string format and flattens these nested json columns in a Dataframe (eg: Struct type columns). 
Just pass the dataframe containing the Nested Columns as parameter. <BR>
  
>>** Parameters Needed: **
 * **Serialized Json Data Frame (df):** The Dataframe containing the desired columns that you need deserialized and un-nested. A new Dataframe will be returned.
  
>>** Example Code: ** <BR>
 df_Final = parseJSONColumns( df_SerializedColumns )
  
