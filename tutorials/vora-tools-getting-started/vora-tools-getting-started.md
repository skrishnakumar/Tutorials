## Title: Getting started with SAP HANA Vora Tools

## Details
### You will learn  
You will learn how to start SAP HANA Vora Tools and using two of them: SQL Editor and Data Browser.

### Time to Complete
**10 Min**.

---

1. The **SAP HANA Vora Tools** provide a web UI for viewing and exporting data in tables and views, an SQL editor for creating and running SQL scripts, and a modeler for creating data models.

2. Open Vora Tools from the url http://hostname:9225
username : vora
password : voravora

3. Once Vora Tools opens up in a new browser window, check its **Connection Status** is OK before working with any of its tools.

    Each tool can be opened from the Home screen, or - alternatively - from shortcut icons on the left.

    ![Opening SAP HANA Vora Tools from CAL cockpit](voratools02.jpg)

4. First you will work with SQL Editor, so open it by clicking either on a tile `SQL Editor` or on a shortcut.

    In order to work with your Vora tables, created using Zeppelin in the previous tutorial, you have to register those tables first:
    ```sql
    REGISTER ALL TABLES using com.sap.spark.vora;
    ```
    > Spark SQL supports operating on a variety of data sources. Registering a table allows you to run SQL queries over its data.

5. Run the following command to make sure you don't have the `CUSTOMER_TEXT` table already created on your Vora engine.
    ```sql
    DROP TABLE CUSTOMER_TEXT;
    ```

    Then create the table and check its content.
    ```sql
    CREATE TABLE CUSTOMER_TEXT
    (LANGU string, CUSTOMER_ID string, TEXT string)
    USING com.sap.spark.vora
    OPTIONS (tableName "CUSTOMER_TEXT", paths "/user/vora/customer_text_data.csv");

    SELECT * FROM CUSTOMER_TEXT;
    ```

6. Now open **Data Browser** tool. You should see all available tables and clicking on `CUSTOMER` table will open its content. You can explore the data now.

    ![Browsing data](voratools04.jpg)

## Next Steps
 - [Getting started with SAP HANA Vora Modeler: Creating SQL views](/tutorials/vora-modeler-getting-started/vora-modeler-getting-started.md)
