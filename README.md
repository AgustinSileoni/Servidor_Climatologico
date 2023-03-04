# Servidor_Climatologico
Servidor backend de información climatológica

Deberá armar un servicio de consulta de estado del clima para varias ciudades de Argentina

Para ello tomara la información del servicio meteorológico nacional en forma de archivo, lo procesara y generará una respuesta con formato Json que contenga la información del clima.

En la dirección web https://www.smn.gob.ar/descarga-de-datos hay una serie de archivos disponbiles para descargar. Deberá descargar el archivo de estado de tiempo presente, que es actualizado en forma horaria, por lo que deberá tener programada la descarga del mismo con esa frecuencia. También deberá descargar el archivo de datos meteorológicos del día anterior, que trae los datos en forma horaria para el día anterior de las localidades que el servicio lleva información. El tercer archivo es el pronóstico a 5 días. Este último junto con el de día anterior solo deberá descargarse en forma diaria. El archivo de datos del día anterior deberá registrarse diariamente en una base de datos para mantener la información diaria.

Para el proceso de descarga de archivos y extracción de información de estos (y almacenamiento en la base de datos) será conveniente el uso de expresiones regulares. Utilice módulos para servicios de descarga desde el protocolo https y para la conexión a la base de datos para almacenar los datos y luego consultarlos desde alli. Esta puede ser mysql, postgre o sqlite, la que prefiera.

La consulta deberá ser hecha sobre un URI con diversas opciones y estará programada en Rust utilizando el framework Rokcet https://rocket.rs/ con el formato REST API. La respuesta de los contenidos a entregar depende del URI y sus opciones solicitado al servidor. La localidad a consultar debe venir como un parámetro en la URI (ejemplo http://miservicio/laplata/xxxx) donde la información especifica sea solicitada a través de los valores especificados en la parte xxxx, los cuales pueden ser: pronóstico, estado actual, historia de temperatura, velocidad y dirección del viento y lluvias de los últimos 5 / 10 / 30 días.

Para el hosting del sistema puede utilizar alguno propio, o bien solicitar un servicio gratuito (AWS o similar) o en un servidor de la Facultad.