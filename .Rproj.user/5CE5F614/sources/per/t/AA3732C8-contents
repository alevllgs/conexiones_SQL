# Instala y carga los paquetes necesarios

library(DBI)
library(RMySQL)

# Establece la conexión a MySQL
con <- dbConnect(RMySQL::MySQL(), 
                 user="root", 
                 password="clave", 
                 host="127.0.0.1")

# Crea la base de datos "listado_mascotas" (si no existe)
dbExecute(con, "CREATE DATABASE IF NOT EXISTS PPV")

# Selecciona la base de datos "listado_mascotas"
dbExecute(con, "USE PPV")


# Define la estructura de la tabla
dbExecute(con, "CREATE TABLE IF NOT EXISTS prestaciones_valoradas (
                 run_beneficiario VARCHAR(255),
                 sexo VARCHAR(255),
                 prevision VARCHAR(255),
                 edad INT,
                 fecha_de_otorgamiento DATE,
                 establecimiento VARCHAR(255),
                 compra VARCHAR(255),
                 prestador VARCHAR(255),
                 no_ps INT,
                 problema_de_salud_programa_no_ges VARCHAR(255),
                 cod_is INT,
                 int_sanitaria_is VARCHAR(255),
                 codigo_trazadora INT,
                 glosa_trazadora VARCHAR(255),
                 codigo_familia INT,
                 familia VARCHAR(255),
                 cantidad INT,
                 precio INT,
                 total INT,
                 causal_de_rechazo VARCHAR(255),
                 mes INT,
                 archivo INT,
                 origen VARCHAR(255),
                 cat_final VARCHAR(255),
                 clasificacion VARCHAR(255),
                 comuna VARCHAR(255),
                 id INT AUTO_INCREMENT PRIMARY KEY
                 )")

# Pasa el DataFrame completo a la tabla en MySQL
#dbWriteTable(con, "listado_mascotas", mascotas, append = TRUE, row.names = FALSE)
dbWriteTable(con, "prestaciones_valoradas", mega_base, row.names=FALSE, append=TRUE)

# Cierra la conexión
dbDisconnect(con)



# Esta conexion resulto funciona correctamente

