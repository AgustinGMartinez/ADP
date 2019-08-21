# Servicios requeridos para todo esto:

```ref2: todos los que tienen esta referencia usan el mismo servicio para enviar datos, de hecho todos los post viejos usan este servicio, mandando datos diferentes. No lo probé, pero intuyo que admite datos parciales, es decir, acepta cualquier cosa que le mandes y lo guarda aunque sean cosas de distintas secciones. No se como identifica cada cosa. Los xml del 1 al 5 hacen uso de este servicio, excepto el xml3.```

### Acceso web

Tipo | Estado| Funcion | Observaciones | Api Manager
--- | --- | --- | --- | ---
Post | No existe | Cambia la contraseña del prestador | Debe recibir y corroborar contraseña actual.

### Dirección Personal

Tipo | Estado| Funcion | Observaciones | Api Manager
--- | --- | --- | --- | ---
Get | Migrado | Obtener provincia, partido, localidad, calle, numero, piso, depto, CP y telefono **PERSONALES** del prestador | JBOSS5BACKEND."/svc-smmp-busqueda-prestadores/medicoAsistencial/{prestador}/normalizado" | /V1.0/prestadores/1130?traer-calificaciones=true
Get | En SGI | Obtener listado de provincias | /ws.situacion-terapeutica/rest-api/provincias (usa id_presmed) |
Get | En SGI | Obtener listado de partidos | /ws.gis/api/paises/{codigo_pais}/provincias/{codigo_provincia}/partidos
Get | En SGI | Obtener listado de localidades | /ws.gis/api/paises/{codigo_pais}/provincias/{codigo_provincia}/partidos/{codigo_partido}/localidades
Get | En SGI | Obtener listado de barrios | /ws.gis/api/paises/{codigo_pais}/provincias/{codigo_provincia}/localidades/{codigo_localidad}/barrios
Get | No existe | Obtener listado de sexos | -
Get | Mockeado, ex JBOSS5 pero hardcodeado el servicio | Obtener listado de tipos de documentos | JBOSS5BACKEND/maestros/datos/tiposdocumentacion | /v0/maestros/documentos/tipos
Get | Existe en SGI | Validador de telefonos | /ws.telefonos/api/validar
Get | Existe en SGI | Validador de domicilios | /ws.gis/api/validar.xml
Get | Existe en jboss5 | Obtener listado de idiomas seleccionables | JBOSS5BACKEND/svc-smmp-busqueda-prestadores/prestador/{prestador}/idiomas-por-prestador
Post | Existe en jboss5 pero ver ref2 | Guardar provincia, partido, localidad, calle, numero, piso, depto, CP y telefono **PERSONALES** del prestador | JBOSS5BACKEND/smmp-adp-integration/"

### Dirección de la Correspondencia

Tipo | Estado| Funcion | Observaciones | Api Manager
--- | --- | --- | --- | ---
Get | Existe en jboss5 | Obtiene los datos de direccion de correspondencia del prestador, a saber, provincia, partido, localidad, calle, numero, piso, depto, CP y telefono | JBOSS5BACKEND/svc-smmp-busqueda-prestadores/prestador/{prestador}/dom-corresp
Post | Existe en jboss5 pero ver ref2 | Guarda los datos de direccion de correspondencia del prestador, a saber, provincia, partido, localidad, calle, numero, piso, depto, CP y telefono | JBOSS5BACKEND/smmp-adp-integration/"

### Lugares de atencion

Tipo | Estado| Funcion | Observaciones | Api Manager
--- | --- | --- | --- | ---
Get | Existe en jboss5 | Trae los lugares de atencion con sus datos | JBOSS5BACKEND/svc-smmp-busqueda-prestadores/medicoAsistencial/lugaresDeAtencion/{prestador}
Get | No existe, hardcodeado | Trae tipos de lugares | Las opciones hardcodeadas son "consultorio" e "institucion". No se qué valor les corresponde en la base de datos.
Post | Existe en jboss5 pero ver ref2 | guarda nuevo lugar de atencion, los datos que envia son: tipo de lugar, provincia, partido, localidad, calle, numero, piso, depto, codigo postal, telefono principal y 3 telefonos alternativos opcionales, fecha de habilitacion y 1 o más imagenes que corresponden al certificado de habilitacion | JBOSS5BACKEND/smmp-adp-integration/"

### Datos personales

Tipo | Estado| Funcion | Observaciones | Api Manager
--- | --- | --- | --- | ---
Get | Migrado | Traer datos **personales** del prestador, a saber: nombre, apellido, fecha de nacimiento, tipo y numero de documento, estado civil, sexo, nacionalidad, telefono celular. | JBOSS5BACKEND."/svc-smmp-busqueda-prestadores/medicoAsistencial/{prestador}/normalizado" | /V1.0/prestadores/1130?traer-calificaciones=true
Post | Existe en jboss5 pero ver ref2 | guarda los datos de arriba | JBOSS5BACKEND/smmp-adp-integration/"

### Datos Profesionales

Tipo | Estado| Funcion | Observaciones | Api Manager
--- | --- | --- | --- | ---
Get | Migrado | Traer datos **profesionales** del prestador, a saber: matricula nacional y provincial, provincia, email | JBOSS5BACKEND."/svc-smmp-busqueda-prestadores/medicoAsistencial/{prestador}/normalizado" | /V1.0/prestadores/1130?traer-calificaciones=true
Get | Mockeado, ex JBOSS5 | Traer idiomas que habla el prestador | /svc-smmp-busqueda-prestadores/prestador/$codPres/idiomas-por-prestador | /v0/prestador/1130/idiomas
Post | Existe en jboss5 pero ver ref2 | guarda los datos de arriba | JBOSS5BACKEND/smmp-adp-integration/"

### Estado de Trámites

Tipo | Estado| Funcion | Observaciones | Api Manager
--- | --- | --- | --- | ---
Get | Existe en jboss5 | Trae estado de tramites de prestador | JBOSS5BACKEND/svc-smmp-prestadores-actdat/act-datos-prestadores/consulta/tramites
Get | Existe en jboss5 | Trae detalle del tramite del prestador | JBOSS5BACKEND/svc-smmp-prestadores-actdat/act-datos-prestadores/consulta/detalle-tramite

### Configuraciones

Tipo | Estado| Funcion | Observaciones | Api Manager
--- | --- | --- | --- | ---
Get | Migrado | Trae si el prestador cumple los requisitos para ser calificado | -
Get | Migrado | Trae configuracion de si el prestador esta mostrando su calificacion o no | -
Get/Delete | Totalmente migrado | Da de alta o baja la configuracion de si el prestador muestra o no su calificacion | -
Get | No existe | Trae configuracion del prestador, a saber: si publica su imagen en cartilla (o no), si usa DrApp (o no), si publica sus idiomas en cartilla (o no) | -
Post | No existe | Modifica la configuracion anterior | -

### Baja del prestador

Tipo | Estado| Funcion | Observaciones | Api Manager
--- | --- | --- | --- | ---
Post | Existe en jboss5 pero ver ref2 | Da de baja el prestador | JBOSS5BACKEND/smmp-adp-integration/"

### Imagen del prestador

Tipo | Estado| Funcion | Observaciones | Api Manager
--- | --- | --- | --- | ---
Post | Existe en jboss5 pero ver ref2 | Cambia la imagen del prestador a una nueva | JBOSS5BACKEND/smmp-adp-integration/"

Endpoint con restriccion (que creo que no anda): generarUrl


# Visual: vistas que se corresponden

### En php (1 pagina):

![alt text](https://github.com/AgustinGMartinez/ADP/blob/master/old_datospersonales.PNG?raw=true)

### En react (acceso web es 1 pagina, y las otras dos son 1 sola pagina tambien, 2 total):

![alt text](https://github.com/AgustinGMartinez/ADP/blob/master/new_accesoweb.PNG?raw=true)
--------------------------------
![alt text](https://github.com/AgustinGMartinez/ADP/blob/master/new_datospersonales.PNG?raw=true)
--------------------------------
![alt text](https://github.com/AgustinGMartinez/ADP/blob/master/new_datosprofesionales.PNG?raw=true)

***

### En php (3 paginas):

![alt text](https://github.com/AgustinGMartinez/ADP/blob/master/old_domiciliopersonal.PNG?raw=true)
--------------------------------
![alt text](https://github.com/AgustinGMartinez/ADP/blob/master/old_domiciliocorrespondencia.PNG?raw=true)
--------------------------------
![alt text](https://github.com/AgustinGMartinez/ADP/blob/master/old_lugaresdeatencion.PNG?raw=true)

### En react (las 3 son 1 sola pagina):

![alt text](https://github.com/AgustinGMartinez/ADP/blob/master/new_direccionpersonal.PNG?raw=true)
--------------------------------
![alt text](https://github.com/AgustinGMartinez/ADP/blob/master/new_direccioncorrespondencia.PNG?raw=true)
--------------------------------
![alt text](https://github.com/AgustinGMartinez/ADP/blob/master/new_lugaresdeatencion.PNG?raw=true)

***

### En php (1 pagina):

![alt text](https://github.com/AgustinGMartinez/ADP/blob/master/old_tramites.PNG?raw=true)

### En react (1 pagina):

![alt text](https://github.com/AgustinGMartinez/ADP/blob/master/new_tramites.PNG?raw=true)

***

### En php (1 pagina):

![alt text](https://github.com/AgustinGMartinez/ADP/blob/master/old_baja.PNG?raw=true)

### En react (1 pagina):

![alt text](https://github.com/AgustinGMartinez/ADP/blob/master/new_baja.PNG?raw=true)

***

### En php (1 pagina):

![alt text](https://github.com/AgustinGMartinez/ADP/blob/master/old_foto.PNG?raw=true)

### En react (padre de todas las paginas):

![alt text](https://github.com/AgustinGMartinez/ADP/blob/master/new_perfil.PNG?raw=true)

***

### Todas las demas vistas no tienen correspondiente por ser implementación nueva.
