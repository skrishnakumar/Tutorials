---
title: Loading sample data from different file formats
description: You will use Apache Zeppelin to create tables and load sample data from files in different file formats already created in HDFS in SAP HANA Vora, developer edition, on CAL.
tags: [  tutorial>beginner, topic>big-data, products>sap-hana-vora ]
---
## Prerequisites  
 - **Proficiency:** Beginner
 - **Tutorials:** [SAP HANA Vora Modeler: Aggregation in SQL View](http://www.sap.com/developer/tutorials/vora-modeler-view-aggregate.html)

## Next Steps
 - [Using hierarchies in SAP HANA Vora](http://www.sap.com/developer/tutorials/vora-zeppelin-hierarchies.html)

## Details
### You will learn  
You will learn how to load sample data from Parquet and ORC file formats.

### Time to Complete
**5 Min**.

---

1. Similarly to loading sample CSV files you will use Zeppelin with predefined notebook here as well. Open Zeppelin from the url http://hostname:9099

    Once Zeppelin opens up in a new browser window, check it is **Connected** and if yes, then click on `2_DataTypes` notebook.

    ![Open Zeppelin](voraformats01.jpg)
    
2. For this tutorial, sample files are preloaded into HDFS. You can see them by executing following statements in the Zeppelin
    ```shell
    %sh
    hdfs dfs -ls *.orc
    hdfs dfs -ls *.parquet
    ```
    Your output will match the screenshot below.
     ![Check HDFS for files](voraformats00.jpg)

3. Now you will create a table `SALES_P` using Apache Parquet file format.

    Click on **Run this paragraph** play button first on `CREATE TABLE` statement and then on `SELECT` one. Please note `format "parquet"` option in the first statement.

    ![Running Parquet file load](voraformats02.jpg)

    You can run these statements from SAP HANA Vora Tools' SQL Editor as well.

    ```sql
    CREATE TABLE SALES_P(CUSTOMER_ID string, YEAR string, REVENUE bigint)
    USING com.sap.spark.vora
    OPTIONS(tablename "SALES_P", paths "/user/vora/sales_p.parquet/*",format "parquet");

    SELECT * FROM SALES_P

    ```

4. Next you will create table `SALES_O` using Apache ORC (Optimized Record Columnar File) file format.

    Click on **Run this paragraph** play button first on `CREATE TABLE` statement and then on `SELECT` one. Please note `format "orc"` option in the first statement.

    ![Running ORC file load](voraformats03.jpg)

    You can run these statements from SAP HANA Vora Tools' SQL Editor as well.

    ```sql
    CREATE TABLE SALES_O(CUSTOMER_ID string, YEAR string, REVENUE bigint)
    USING com.sap.spark.vora
    OPTIONS (tablename "SALES_O",paths "/user/vora/sales_O.orc/*",format "orc");

    SELECT * FROM SALES_O

    ```    

## Next Steps
 - [Using hierarchies in SAP HANA Vora](http://www.sap.com/developer/tutorials/vora-zeppelin-hierarchies.html)
