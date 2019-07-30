# Servicios requeridos para todo esto:

```ref1: todos los que tienen esta referencia usan el mismo servicio para obtener datos, es un servicio que trae un monton de datos que se necesitan en distintas pantallas. El unico "problema" es que trae más datos de los que se necesita en cada pantalla. ```

```ref2: todos los que tienen esta referencia usan el mismo servicio para enviar datos, de hecho todos los post viejos usan este servicio, mandando datos diferentes. No lo probé, pero intuyo que admite datos parciales, es decir, acepta cualquier cosa que le mandes y lo guarda aunque sean cosas de distintas secciones. No se como identifica cada cosa. Los xml del 1 al 5 hacen uso de este servicio, excepto el xml3.```

### Acceso web

Tipo | Estado| Funcion | Observaciones
--- | --- | --- | ---
Post | No existe | Cambia la contraseña del prestador | Debe recibir y corroborar contraseña actual.

### Direccion Personal

Tipo | Estado| Funcion | Observaciones
--- | --- | --- | ---
Get | Existe en jboss5 pero ver ref1 | Obtener provincia, partido, localidad, calle, numero, piso, depto, CP y telefono **PERSONALES** del prestador | -
Get | Existe en jboss5 | Obtener listado de provincias | -
Get | Existe en jboss5 | Obtener listado de partidos | -
Get | Existe en jboss5 | Obtener listado de localidades | -
Get | No existe | Obtener listado de sexos | -
Get | Existe en jboss5 pero el servicio está hardcodeado | Obtener listado de tipos de documentos | -
Get | Existe en jboss5 | Obtener listado de idiomas seleccionables | -
Post | Existe en jboss5 pero ver ref2 | Guardar provincia, partido, localidad, calle, numero, piso, depto, CP y telefono **PERSONALES** del prestador | -

### Direccion Correspondencia

Tipo | Estado| Funcion | Observaciones
--- | --- | --- | ---
Get | Existe en jboss5 | Obtiene los datos de direccion de correspondencia del prestador, a saber, provincia, partido, localidad, calle, numero, piso, depto, CP y telefono | -
Post | Existe en jboss5 pero ver ref2 | Guarda los datos de direccion de correspondencia del prestador, a saber, provincia, partido, localidad, calle, numero, piso, depto, CP y telefono | -

### Lugares de atencion

Tipo | Estado| Funcion | Observaciones
--- | --- | --- | ---
Get | Existe en jboss5 | Trae los lugares de atencion con sus datos | -
Get | No existe, hardcodeado | Trae tipos de lugares | Las opciones hardcodeadas son "consultorio" e "institucion". No se qué valor les corresponde en la base de datos.
Post | Existe en jboss5 pero ver ref2 | guarda nuevo lugar de atencion, los datos que envia son: tipo de lugar, provincia, partido, localidad, calle, numero, piso, depto, codigo postal, telefono principal y 3 telefonos alternativos opcionales, fecha de habilitacion y 1 o más imagenes que corresponden al certificado de habilitacion | -

### Datos personales

Tipo | Estado| Funcion | Observaciones
--- | --- | --- | ---
Get | Existe en jboss5 pero ver ref1 | Traer datos **personales** del prestador, a saber: nombre, apellido, fecha de nacimiento, tipo y numero de documento, estado civil, sexo, nacionalidad, telefono celular. | -
Post | Existe en jboss5 pero ver ref2 | guarda los datos de arriba | -

### Direccion Profesionales

Tipo | Estado| Funcion | Observaciones
--- | --- | --- | ---
Get | Existe en jboss5 pero ver ref1 | Traer datos **profesionales** del prestador, a saber: matricula nacional y provincial, provincia, email y todos los idiomas del prestador | -
Post | Existe en jboss5 pero ver ref2 | guarda los datos de arriba | -

### Estado de Trámites

Tipo | Estado| Funcion | Observaciones
--- | --- | --- | ---
Get | Existe en jboss5 | Trae estado de tramites de prestador | -

### Configuraciones

Tipo | Estado| Funcion | Observaciones
--- | --- | --- | ---
Get | Totalmente migrado | Trae si el prestador cumple los requisitos para ser calificado | -
Get | Totalmente migrado | Trae configuracion de si el prestador esta mostrando su calificacion o no | -
Get/Delete | Totalmente migrado | Da de alta o baja la configuracion de si el prestador muestra o no su calificacion | -
Get | No existe | Trae configuracion del prestador, a saber: si publica su imagen en cartilla (o no), si usa DrApp (o no), si publica sus idiomas en cartilla (o no) | -
Post | No existe | Modifica la configuracion anterior | -

### Baja del prestador

Tipo | Estado| Funcion | Observaciones
--- | --- | --- | ---
Post | Existe en jboss5 pero ver ref2 | Da de baja el prestador | -

### Imagen del prestador

Tipo | Estado| Funcion | Observaciones
--- | --- | --- | ---
Post | Existe en jboss5 pero ver ref2 | Cambia la imagen del prestador a una nueva | -
