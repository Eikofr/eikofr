SELECT *
FROM (
  SELECT table_name, column_name
  FROM information_schema.columns
  WHERE table_schema NOT IN ('pg_catalog', 'information_schema')
) AS cols
WHERE EXISTS (
  SELECT *
  FROM pg_tables
  WHERE tablename = cols.table_name
  AND EXISTS (
    SELECT *
    FROM pg_attribute
    WHERE attrelid = CONCAT(cols.table_name, '::regclass')::oid
    AND attname = cols.column_name
    AND EXISTS (
      SELECT *
      FROM "public"."%I" AS t
      WHERE t.%I = %L
    )
  )
)
