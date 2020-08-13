# The ON COMMIT command
TEMP tables in postgres are handy for tests and partially transformed data because they get cleaned up automatically after each session. However, if you are doing certain tasks within a transaction and want to make sure the table get destroyed once the transaction ends, you can use the `ON COMMIT DROP` command e.g.

```sql
BEGIN;
CREATE TEMP TABLE test (
  id UUID,
  field_1 VARCHAR,
  field_2 NUMERIC
  --- ...
) ON COMMIT DROP;

COMMIT;
```
