library(DBI)
library(RPostgres)

# Crear el data.frame
nombres <- c("Alice", "Bob", "Charlie", "David", "Eva", "Frank", "Grace", "Hannah", "Ivy", "Jack")
edades <- c(25, 32, 28, 45, 30, 37, 22, 29, 34, 40)
fechas <- c("2024-01-01 10:00:00", "2024-01-02 11:30:00", "2024-01-03 14:45:00", 
            "2024-01-04 09:15:00", "2024-01-05 16:00:00", "2024-01-06 08:30:00", 
            "2024-01-07 13:45:00", "2024-01-08 12:00:00", "2024-01-09 15:30:00", 
            "2024-01-10 10:45:00")

datos <- data.frame(nombre = nombres, edad = edades, fecha = as.POSIXct(fechas))

# Establecer la conexión a la base de datos
con <- dbConnect(RPostgres::Postgres(),
                 dbname = "sigcom",
                 host = "localhost",
                 port = 5432,
                 user = "postgres",
                 password = "alevllgs")

# Crear la tabla si no existe
create_table_query <- "
CREATE TABLE IF NOT EXISTS conexion_r (
    id SERIAL PRIMARY KEY,
    nombre VARCHAR(255),
    edad INT,
    fecha TIMESTAMP
);
"
dbExecute(con, create_table_query)

# Insertar valores en la tabla
for (i in 1:nrow(datos)) {
  query <- sprintf("INSERT INTO conexion_r (nombre, edad, fecha) VALUES ('%s', %d, '%s')",
                   datos$nombre[i], datos$edad[i], format(datos$fecha[i], "%Y-%m-%d %H:%M:%S"))
  dbExecute(con, query)
}

# Verificar que los valores se han insertado
result <- dbGetQuery(con, "SELECT * FROM conexion_r")
print(result)

# Cerrar la conexión
dbDisconnect(con)


