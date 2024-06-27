Todo el trabajo se hizo en un .ipynb por la facilidad de ejecutar codigo por celdas.

#   ETL
Se importa Pandas para poder leer el .csv, muestro las columnas para interiorisar los datos y se agrega una columna numerica para el tipo de pago. esto ayuda para poder tener un acceso simple a los metodos de pago. hice una lista de 0,1,2 que serian Credit Card, PayPal y Debit Card.

#   Postgresql
Importo create_engine, que sirve para crear un puntero y poder conectarse e interactuar con la base de datos, Text, que sirve para que tome el formato str al formato sql y el metodo inspect que sirve para obtener metodos que me muestren los metadatos de los objetos en SQL.
Creo el engine y armo la URL para poder entrar a Postgres, el nombre, contraseña, el puerto, el host y el nomrbe de la base de datos, creada directamente desde pgadmin4.
Con df.to_sql lo que hago es crear la tabla con todas las columnas y sus tipos de datos.
Me aseguro que se creo correctamente con inspect, le doy el engine como parametro y despues le digo que me muestre los nombres de las tablas. Luego veo si esta bien guardada la informacion.

# Problemas
Se conecta a la base de datos y se realiza una query, en este caso la query agarra Total Revenue como la sumatoria dividida entre la Region y las Categorias. Vease como se usa text con la cadena de texto que tiene el query.

En el segundo problema para optimizar la query primero pense si era necesario que se cuenten los NULLs, el SUM los ignora, al no necesitar su total y solo necesito la suma se puede olvidar tranquilamente, en caso contrario de que necesite el total de valores para sacar el promedio se puede usar la funcion COALESCE que transforma los NULL en 0 pero no los olvida como SUM (SELECT category, SUM(COALESCE(total_price, 0)) AS total_price_sum).

# Interpretacion de los graficos
