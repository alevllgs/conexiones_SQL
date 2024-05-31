library(DBI)
library(RPostgres)

# Establecer la conexión a la base de datos
con <- dbConnect(RPostgres::Postgres(),
                 dbname = "sigcom",
                 host = "localhost",
                 port = 5432,
                 user = "postgres",
                 password = "clave")

# Crear la tabla
query <- "
CREATE TABLE conexion_r (
    id SERIAL PRIMARY KEY,
    nombre VARCHAR(255),
    edad INT,
    fecha TIMESTAMP
);
"
dbExecute(con, query)

# Verificar que la tabla se ha creado
tables <- dbListTables(con)
print(tables)

# Cerrar la conexión
dbDisconnect(con)

