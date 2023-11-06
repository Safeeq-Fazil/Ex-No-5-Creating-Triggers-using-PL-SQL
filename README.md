# Ex. No: 5 Creating Triggers using PL/SQL

## Date: 1/9/2023

## AIM: To create a Trigger using PL/SQL.
### Steps:

1.Create employee table with following attributes (empid NUMBER, empname VARCHAR(10), dept VARCHAR(10),salary NUMBER);

2.Create salary_log table with following attributes (log_id NUMBER GENERATED ALWAYS AS IDENTITY, empid NUMBER,empname VARCHAR(10),old_salary NUMBER,new_salary NUMBER,update_date DATE);

3.Create a trigger named as log_salary-update.

4.Inside the trigger block, Insert the values into the salary_log table whenever the salary is updated.

5.End the trigger.

6.Update the salary of an employee in employee table.

7.Whenever a salary is updated for the employee it must be logged into the salary_log table with old salary and new salary.

8.Display the employee table, salary_log table.

## Program:
```
CREATE TABLE employed(
  empid NUMBER,
  empname VARCHAR2(10),
  dept VARCHAR2(10),
  salary NUMBER
);

CREATE TABLE sal_log (
  log_id NUMBER GENERATED ALWAYS AS IDENTITY,
  empid NUMBER,
  empname VARCHAR2(10),
  old_salary NUMBER,
  new_salary NUMBER,
  update_date DATE
);
```
### Create employee table

![image](https://github.com/Safeeq-Fazil/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/118680361/1aab3ea7-63e6-4523-9eaf-f327c13f0074)


### Create salary_log table

![image](https://github.com/Safeeq-Fazil/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/118680361/6885b39b-aef3-4f75-84d9-ac9777a6d84d)


### PLSQL Trigger code
```
->Create the trigger
Create the trigger
CREATE OR REPLACE TRIGGER log_sal_update
BEFORE UPDATE ON employed
FOR EACH ROW
BEGIN
  IF :OLD.salary != :NEW.salary THEN
    INSERT INTO sal_log (empid, empname, old_salary, new_salary, update_date)
    VALUES (:OLD.empid, :OLD.empname, :OLD.salary, :NEW.salary, SYSDATE);
  END IF;
END;
/
->Update the salary of an employee
UPDATE employed
SET salary = 60000
WHERE empid = 1;
->Display the employee table
SELECT * FROM employed;

->Display the salary_log table
SELECT * FROM sal_log;
```
### Output:

![image](https://github.com/Safeeq-Fazil/Ex-No-5-Creating-Triggers-using-PL-SQL/assets/118680361/e27dcca0-7fe0-4e0d-9660-eabf2da9cfac)


### Result:

The program has been implemented successfully.
