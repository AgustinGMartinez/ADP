# Servicios requeridos para todo esto:

```ref2: todos los que tienen esta referencia usan el mismo servicio para enviar datos, de hecho todos los post viejos usan este servicio, mandando datos diferentes. No lo probé, pero intuyo que admite datos parciales, es decir, acepta cualquier cosa que le mandes y lo guarda aunque sean cosas de distintas secciones. No se como identifica cada cosa. Los xml del 1 al 5 hacen uso de este servicio, excepto el xml3.```

### Pendientes (en orden de prioridadad)

```1``` ```2```

### Acceso web

N | Tipo | Estado| Funcion | Observaciones | Api Manager
--- | --- | --- | --- | --- | ---
1 | Post | No existe | Cambia la contraseña del prestador | Debe recibir y corroborar contraseña actual.

### Dirección Personal

N | Tipo | Estado| Funcion | Observaciones | Api Manager
--- | --- | --- | --- | --- | ---
2 | Get | Migrado | Obtener provincia, partido, localidad, calle, numero, piso, depto, CP y telefono **PERSONALES** del prestador | JBOSS5BACKEND."/svc-smmp-busqueda-prestadores/medicoAsistencial/{prestador}/normalizado" | /V1.0/prestadores/1130?traer-calificaciones=true
3 | Get | En SGI | Obtener listado de provincias | /ws.situacion-terapeutica/rest-api/provincias (usa id_presmed) |
4 | Get | En SGI | Obtener listado de partidos | /ws.gis/api/paises/{codigo_pais}/provincias/{codigo_provincia}/partidos
5 | Get | En SGI | Obtener listado de localidades | /ws.gis/api/paises/{codigo_pais}/provincias/{codigo_provincia}/partidos/{codigo_partido}/localidades
6 | Get | En SGI | Obtener listado de barrios | /ws.gis/api/paises/{codigo_pais}/provincias/{codigo_provincia}/localidades/{codigo_localidad}/barrios
7 | Get | No existe | Obtener listado de sexos | -
8 | Get | En SGI | Obtener listado de tipos de documentos | /ws.prestadores/app/main/prestadores/tipodocumento
9 | Get | En SGI | Validador de telefonos | /ws.telefonos/api/validar
10 | Get | En SGI | Validador de domicilios | /ws.gis/api/validar.xml
11 | Get | En SGI | Obtener listado de idiomas seleccionables | /ws.prestadores/app/main/prestadores/idiomas
12 | Post | Existe en jboss5 pero ver ref2 | Guardar provincia, partido, localidad, calle, numero, piso, depto, CP y telefono **PERSONALES** del prestador | JBOSS5BACKEND/smmp-adp-integration/"

### Dirección de la Correspondencia

N | Tipo | Estado| Funcion | Observaciones | Api Manager
--- | --- | --- | --- | --- | ---
13 | Get | Existe en jboss5 | Obtiene los datos de direccion de correspondencia del prestador, a saber, provincia, partido, localidad, calle, numero, piso, depto, CP y telefono | JBOSS5BACKEND/svc-smmp-busqueda-prestadores/prestador/{prestador}/dom-corresp
14 | Post | Existe en jboss5 pero ver ref2 | Guarda los datos de direccion de correspondencia del prestador, a saber, provincia, partido, localidad, calle, numero, piso, depto, CP y telefono | JBOSS5BACKEND/smmp-adp-integration/"

### Lugares de atencion

N | Tipo | Estado| Funcion | Observaciones | Api Manager
--- | --- | --- | --- | --- | ---
15 | Get | Existe en jboss5 | Trae los lugares de atencion con sus datos | JBOSS5BACKEND/svc-smmp-busqueda-prestadores/medicoAsistencial/lugaresDeAtencion/{prestador}
16 | Get | No existe, hardcodeado | Trae tipos de lugares | Las opciones hardcodeadas son "consultorio" e "institucion". No se qué valor les corresponde en la base de datos.
17 | Get | En SGI | Trae horarios del lugar |  | Pedir a wally
18 | Get | En SGI | Trae telefonos del lugar |  | Pedir a wally
19 | Post | Existe en jboss5 pero ver ref2 | guarda nuevo lugar de atencion, los datos que envia son: tipo de lugar, provincia, partido, localidad, calle, numero, piso, depto, codigo postal, telefono principal y 3 telefonos alternativos opcionales, fecha de habilitacion y 1 o más imagenes que corresponden al certificado de habilitacion | JBOSS5BACKEND/smmp-adp-integration/"

### Datos personales

N | Tipo | Estado| Funcion | Observaciones | Api Manager
--- | --- | --- | --- | ---
20 | Get | Migrado | Traer datos **personales** del prestador, a saber: nombre, apellido, fecha de nacimiento, tipo y numero de documento, estado civil, sexo, nacionalidad, telefono celular. | JBOSS5BACKEND."/svc-smmp-busqueda-prestadores/medicoAsistencial/{prestador}/normalizado" | /V1.0/prestadores/1130?traer-calificaciones=true
21 | Get | En SGI | Trae tipos de estados civiles | /ws.prestadores/app/main/prestadores/civilestado
22 | Get | En SGI | Trae tipos de nacioanlidades | /ws.gis/api/nacionalidades
23 | Post | Existe en jboss5 pero ver ref2 | guarda los datos de arriba | JBOSS5BACKEND/smmp-adp-integration/"

### Datos Profesionales

N | Tipo | Estado| Funcion | Observaciones | Api Manager
--- | --- | --- | --- | ---
24 | Get | Migrado | Traer datos **profesionales** del prestador, a saber: matricula nacional y provincial, provincia, email | JBOSS5BACKEND."/svc-smmp-busqueda-prestadores/medicoAsistencial/{prestador}/normalizado" | /V1.0/prestadores/1130?traer-calificaciones=true
25 | Get | En SGI | Traer idiomas que habla el prestador | /ws.prestadores/app/main/prestadores/1130/idiomas
26 | Post | Existe en jboss5 pero ver ref2 | guarda los datos de arriba | JBOSS5BACKEND/smmp-adp-integration/"

### Estado de Trámites

N | Tipo | Estado| Funcion | Observaciones | Api Manager
--- | --- | --- | --- | --- | ---
27 | Get | Existe en jboss5 | Trae estado de tramites de prestador | JBOSS5BACKEND/svc-smmp-prestadores-actdat/act-datos-prestadores/consulta/tramites
28 | Get | Existe en jboss5 | Trae detalle del tramite del prestador | JBOSS5BACKEND/svc-smmp-prestadores-actdat/act-datos-prestadores/consulta/detalle-tramite

### Configuraciones

N | Tipo | Estado| Funcion | Observaciones | Api Manager
--- | --- | --- | --- | --- | ---
29 | Get | Migrado | Trae si el prestador cumple los requisitos para ser calificado | -
30 | Get | Migrado | Trae configuracion de si el prestador esta mostrando su calificacion o no | -
31 | Get/Delete | Totalmente migrado | Da de alta o baja la configuracion de si el prestador muestra o no su calificacion | -
32 | Get | No existe | Trae configuracion del prestador, a saber: si publica su imagen en cartilla (o no), si usa DrApp (o no), si publica sus idiomas en cartilla (o no) | -
33 | Post | No existe | Modifica la configuracion anterior | -

### Baja del prestador

N | Tipo | Estado| Funcion | Observaciones | Api Manager
--- | --- | --- | --- | --- | ---
34 | Post | Existe en jboss5 pero ver ref2 | Da de baja el prestador | JBOSS5BACKEND/smmp-adp-integration/"

### Imagen del prestador

N | Tipo | Estado| Funcion | Observaciones | Api Manager
--- | --- | --- | --- | --- | ---
35 | Post | Existe en jboss5 pero ver ref2 | Cambia la imagen del prestador a una nueva | JBOSS5BACKEND/smmp-adp-integration/"

Endpoint con restriccion (que creo que no anda): generarUrl


# Visual: vistas que se corresponden

### En php (1 pagina):

![alt text](https://github.com/AgustinGMartinez/ADP/blob/master/old_datospersonales.PNG?raw=true)

### En react (las 2 son 1 sola pagina):

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
