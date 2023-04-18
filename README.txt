DO $$ 
DECLARE 
  tbl text;
  col text;
  query text := '';
BEGIN 
  FOR tbl IN 
    SELECT table_name 
    FROM information_schema.tables 
    WHERE table_schema = 'public' -- Remplacez "public" par le nom de votre schéma 
    AND table_name = 'ma_table' -- Remplacez "ma_table" par le nom de votre table
  LOOP 
    FOR col IN 
      SELECT column_name 
      FROM information_schema.columns 
      WHERE table_name = tbl 
      AND table_schema = 'public' -- Remplacez "public" par le nom de votre schéma 
    LOOP 
      IF query <> '' THEN 
        query := query || ' OR '; 
      END IF; 
      query := query || format('LOWER(%I) LIKE ''%%developpement%%''', col); 
    END LOOP; 
    EXECUTE format('SELECT * FROM %I WHERE %s', tbl, query) 
    USING OUTPUT; 
  END LOOP; 
END $$;
