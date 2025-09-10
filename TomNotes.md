# Steps 

1.  Run Batch Bash script
2. mbz will be written to a location 
3. Run the following 
```bash 
ls - m  > COURSEEXPORT.txt
```
which will generate a comma separated file  
4. Import the txt file into Excel delimited on the ","
5. Split the Column (Text to Column) based on _
***this will separate the key files****

6. Order the Excel document by the Moodle ID
7. Copy the id's into a text file - MOODLE_IDS.txt
8. Open MOODLE_IDs.txt in vi
9. run the regex - %s/\n/","/g
10. remove the trailing ","
11. run the Moodle Query (below) replacing {ADD_IN_MOODLE_ID_NUMBERS} with the listing ID
12.  Merge into Excel..
13.  Finished.. 

### Mapping Fields for Instructure Canvas

| source | sis_id  | short_name | long_name | account_id | user_id | term_id      | 
| ------ | ------- | ---------- | --------- | ---------- | ------- | ------------ | 
| mbz    | idnumber| shortname  | fullname  |            |         |  from source | 

### Moodle Query 

```sql
select id,idnumber,shortname,fullname from mdl_course 
where id in ({ADD_IN_MOODLE_ID_NUMBERS})
order by id asc;
```
