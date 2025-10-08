
## Reto
### SQL Direct
## Descripcion
Connect to this PostgreSQL server and find the flag!

Additional details will be available after launching your challenge instance.
## Solucion
- al iniciar el desafio nos dan una base de datos a la cual conectarnos y una contraseña, en mi caso:
```
`psql -h saturn.picoctf.net -p 63963 -U postgres pico`
```
- cuando me conecto estoy en algo asi como una terminal
- para saber que puedo hacer hago el mismo truco que en el desafio **Specialer**, presiono Tab 2 veces seguidas para ver que comandos tengo
- me aparece lo siguiente:
```
pico=# 
ABORT                      CLUSTER                    DELETE FROM                FETCH                      MOVE                       RESET                      SHOW                       VALUES
ALTER                      COMMENT                    DISCARD                    GRANT                      NOTIFY                     REVOKE                     START                      WITH
ANALYZE                    COMMIT                     DO                         IMPORT FOREIGN SCHEMA      PREPARE                    ROLLBACK                   TABLE                      
BEGIN                      COPY                       DROP                       INSERT INTO                REASSIGN                   SAVEPOINT                  TRUNCATE                   
CALL                       CREATE                     END                        LISTEN                     REFRESH MATERIALIZED VIEW  SECURITY LABEL             UNLISTEN                   
CHECKPOINT                 DEALLOCATE                 EXECUTE                    LOAD                       REINDEX                    SELECT                     UPDATE                     
CLOSE                      DECLARE                    EXPLAIN                    LOCK                       RELEASE                    SET                        VACUUM              
```

- puedo ver que tengo SELECT  entonces pongo en la terminal:  `SELECT * FROM` para indicar que me devuelva todo de una tabla, pero como no se que tablas hay, persiono TAB TAB
```
pico-# SELECT * FROM 
flags                information_schema.  pg_catalog.          pg_toast.            public.   
```

- como veo que esta "flags" lo completo para obtener la bandera:
```
pico=# SELECT * FROM FLAGS;
 id | firstname | lastname  |                address                 
----+-----------+-----------+----------------------------------------
  1 | Luke      | Skywalker | picoCTF{L3arN_S0m3_5qL_t0d4Y_73b0678f}
  2 | Leia      | Organa    | Alderaan
  3 | Han       | Solo      | Corellia
```
## Notas
- Ese luke skywalker guardando los secretos del universo

## Referencias
