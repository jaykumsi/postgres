![Tinitiate POSTGRES Training](images/sqlserver.png)
# POSTGRES TRIGGERS
In PostgreSQL, a trigger is a set of instructions that are automatically executed or fired in response to certain events on a particular table or view. 
Triggers are useful for enforcing complex business rules, maintaining referential integrity, or performing specific actions when certain data changes occur

* **Creating a Trigger**

The basic syntax for creating a trigger in PostgreSQL is as follows:

CREATE [ CONSTRAINT ] TRIGGER trigger_name
    { BEFORE | AFTER | INSTEAD OF } { event [ OR ... ] }
    ON table_name
    [ FROM referenced_table_name ]
    [ NOT DEFERRABLE | [ DEFERRABLE ] { INITIALLY IMMEDIATE | INITIALLY DEFERRED } ]
    [ FOR [ EACH ] { ROW | STATEMENT } ]
    EXECUTE FUNCTION function_name (arguments);
    
BEFORE triggers are fired before the specified event, while AFTER triggers are fired after the event.
INSTEAD OF triggers are used for views and are fired in place of the triggering event.
event can be INSERT, UPDATE, DELETE, or TRUNCATE.
table_name is the name of the table or view on which the trigger is defined.
function_name is the name of the function that will be executed when the trigger fires. 

Example ::
 -- Create a function to be executed by the trigger
CREATE OR REPLACE FUNCTION set_default_value()
RETURNS TRIGGER AS $$
BEGIN
  IF NEW.column_name IS NULL THEN
    NEW.column_name := 'default_value';
  END IF;
  RETURN NEW;
END;
$$ LANGUAGE plpgsql;

-- Create the trigger
CREATE TRIGGER before_insert_trigger
BEFORE INSERT
ON your_table
FOR EACH ROW
EXECUTE FUNCTION set_default_value();


## Viewing Triggers:

You can view the triggers on a table using the following query:

SELECT * FROM information_schema.triggers WHERE table_name = 'your_table';

## Dropping a Trigger:

To remove a trigger, you can use the DROP TRIGGER statement:

DROP TRIGGER trigger_name ON your_table;


