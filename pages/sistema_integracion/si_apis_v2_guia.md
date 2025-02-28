---
title: Connekta - APIs V2
keywords: 
last_updated: Febrero 27, 2025
tags: #[getting_started]
#summary: "Inicio APIs Version 2"
sidebar: sistema_integracion_sidebar
permalink: si_apis_v2_guia.html
folder: sistema_integracion
---

## **Descripción:**

En esta sección se describe el manejo de las APIs Versión dos del sistema de integraciones de Siesa.
Todos los ejemplos se realizan en la herramienta Postman.

Postman: es una herramienta utilizada para probar APIs, permitiendo a los desarrolladores enviar peticiones a servicios web y ver las respuestas. (https://www.postman.com) 

Las API que hacen referencia a las consultas dinámicas, tiene tres apartes; la URL Request donde se muestra el tipo de la petición que es, Ej. GET, y se pone un ejemplo del Endpoint o URL, una nota donde se describen algunos aspectos del microservicio y el uso donde se muestran los ejemplos de como utilizar el microservicio.

Este documento se organizo como esta definida la Colección en Postman que elaboro el Equipo Connekta, los diferentes microservicios se irán añadiendo a este documento hasta completarlos.


## **CONNEKTA**
###  **Información**

**Motor**:  SQL Server

**Autenticación**: Para ejecutar todas las APIs se requiere el uso de Connikey y ConniToken

**base_url_qa**:  https://integradorqa.siesacloud.com/

**base_url_produccion**:  https://integrador.siesacloud.com/

**idCompania**: es la identificación de la Compañía en el sistema de integración


### **Consultas Dinámicas**

#### V3 Consultas Dinamicas

**Request URL**

    Tipo: GET
    URL: {base_url_qa}/api/connekta/v3/consultasporcompania?idCompania={idCompania}

**Notas**:

Listado de consultas asociadas al cliente que tiene disponibles para usar.

Se listan las consultas de lo que el usuario especifico tenga autorizado en permisos.

Es útil para que el cliente analice el listado de consultas que tiene disponible y para que le de permisos a los usuarios que desee.


**Uso**:


{% include inline_image.html
file="API_V2_0001.png" alt="" %}

Son necesarios los datos de autenticación

{% include inline_image.html
file="API_V2_0002.png" alt="" %}
 
#### V3 Ejecutar Consulta Dinamica

**Request URL**

    Tipo: GET
    URL: https://serviciosqa.siesacloud.com/api/connekta/v3/ejecutarconsulta?idCompania=1&descripcion=interfacesysoluciones_terceros&paginacion=numPag=1|tamPag=100

**Notas**:

El funcionamiento natural de la versión tres es manejar querys básicos.

Se aplica mucha generalidad en esta API, para ser compatible con la versión anterior de Connekta. Permite quitar la opción de los parámetros.

También en la consulta se pueden manejar varias Clausulas "Select.." incluso podría llegar hasta procedimientos almacenados.

Se dejo el parámetro de la paginación como opcional, aunque al cliente es mejor sugerirle que lo use, para que el desempeño sea mejor. 
Incluso ni mencionarle que lo puede omitir. Solo se dejo por compatibilidad como se menciono. 

También se pueden ejecutar procedimientos almacenados o mandar a llamar a varias tablas, pero cuando se usa con paginación esto ya no se podría realizar, se puede unicamente cuando se usa sin paginación.

**Uso**:

• Uso Simple, una solo consulta (*)

{% include inline_image.html
file="API_V2_0003.png" alt="" %}
    (*Configuración de la Consulta en el sistema de integración)
 
• Uso de varias consultas al tiempo

{% include inline_image.html
file="API_V2_0004.png" alt="" %}
 
◦ Muestra dos tablas al ejecutar

{% include inline_image.html
file="API_V2_0005.png" alt="" %}

{% include inline_image.html
file="API_V2_0006.png" alt="" %}
 
◦ Si no se quitan los parámetros se presenta el error siguiente al ejecutar

{% include inline_image.html
file="API_V2_0007.png" alt="" %}


#### V3.0.1 Ejecutar Consulta Dinamica Cache

**Request URL**


    Tipo: GET
    URL: https://serviciosqa.siesacloud.com/api/connekta/v3.0.1/ejecutarconsulta?idCompania=1&descripcion=interfacesysoluciones_terceros&paginacion=numPag=1|tamPag=100 

**Notas**:

Se extendio el API V3 Ejecutar Consulta Dinámica con el manejo del Cache, y la paginación es requerida. 

Es decir, se agrego a la versión 3 en la versión 3.0.1 la naturaleza del funcionamiento en cache, que consiste en que se hace el llamado a la base de datos en la página 1, y este llamado o la información es guardada en cache para que a partir de la página 2 la aplicación no vaya a la base de datos, sino que consulte la información en memoria (cache) dando el resultado mucho mas rápido y consumiendo menos recursos. 

El cache tiene dos vencimientos:

El primero es cuando se envía la página 1, en ese momento, borra el cache y lo carga de nuevo desde la base de datos.

Y el segundo se maneja en una variable en los headers del uso del API llamado "Connekta-Cache-Time-Remaining" variable que maneja el tiempo que permanece la información en cache, cuando este tiempo expira se elimina la información del cache y se vuelve a leer y cargar en cache la información desde la base de datos. 

En Connekta, en la documentación siempre se garantiza que inicie desde la página uno.

**Uso**:

{% include inline_image.html
file="API_V2_0009.png" alt="" %}

• Variables en Headers

{% include inline_image.html
file="API_V2_0010.png" alt="" %}

    Connekta-Rate-Limit-Limit | Limite de peticiones por minuto 
    Connekta-Rate-Limit-Remaining | Peticiones faltantes en el minuto actual
    Connekta-Rate-Limit-Reset | Tiempo en que se reinicia el limit 
    Connekta-Cache-Time-Remaining | tiempo en cache de la informacion antes de expirar.


Estas variables se usan para evitar ataques de uso simultaneo.

Cuando se agota el limite de las peticiones en el tiempo dado, el Microservicio muestra lo siguiente Mensaje:

{% include inline_image.html
file="API_V2_0011.png" alt="" %}

En este caso el limite estaba en 10.

#### V3.1 Ejecutar Consulta Dinamica

**Request URL**

    Tipo: GET
    URL: https://serviciosqa.siesacloud.com/api/connekta/v3.1/ejecutarconsulta?idCompania=1&descripcion=interfacesysoluciones_terceros_paginacion_obligatoria&paginacion=numPag=1|tamPag=100&parametros=Filters = {Filters}

**Notas**:

La versión 3.1 obliga de manera estructural a usar la paginación.

En la versión 3.1 los filtros son dinámicos.

En los filtros se pueden incluir todas las clausulas que se manejan en un Where de SQL. 
Tales como Like, Between, and, or, etc.

Funciona también como las APIs de la versión uno, y se debe mantener para tener compatibilidad con los clientes que ya se hayan manejado con esa versión. Pero en este caso la paginación es obligatoria y los filtros dinámicos.


**Uso**:

Ver la siguiente imagen, se puede notar la paginación y el filtro dinamico (parametros)

{% include inline_image.html
file="API_V2_0013.png" alt="" %}


Consulta Ejemplo

La estructuración del query debe ir de la siguiente forma:

{% include inline_image.html
file="API_V2_0012.png" alt="" %}


Siempre se debe construir las consultas de la siguiente forma:

{% include inline_image.html
file="API_V2_0008.png" alt="" %}

``` sql
-- las consultas se deben construir de esta forma:
DECLARE @numPag	INT = {numPag}
DECLARE @tamPag	INT = {tamPag}
DECLARE @paramOrderPag NVARCHAR(MAX) = 'f200_rowid'
DECLARE @skipReg  INT = (@numPag-1) * @tamPag 
DECLARE @pageLimitSize  INT = 100;
DECLARE @f_filters NVARCHAR(MAX) = {Filters}
DECLARE @query NVARCHAR(MAX) 
DECLARE @sql NVARCHAR(MAX)

BEGIN
	TRY
		IF @tamPag > @pageLimitSize
		BEGIN
			SELECT 'La cantidad de registros solicitados excede el permitido.' AS 'alerta'
		END
		ELSE
		BEGIN
			IF @numPag < 1
				BEGIN
					SELECT 'Sin registros.' AS 'alerta'
				END
			ELSE
			BEGIN							
				SET @sql = '
				SELECT
				*
				FROM
				(
				SELECT
				 t200.f200_id_cia
				,t200.f200_rowid
				,RTRIM(f200_id) AS f200_id
				,RTRIM(f200_nit) AS f200_nit
				,t200.f200_dv_nit
				,t200.f200_id_tipo_ident
				,t200.f200_ind_tipo_tercero
				,RTRIM(t200.f200_razon_social) AS f200_razon_social
				,RTRIM(t200.f200_apellido1) AS f200_apellido1
				,RTRIM(t200.f200_apellido2) AS f200_apellido2
				,RTRIM(t200.f200_nombres) AS f200_nombres
				,t200.f200_ind_cliente
				,t200.f200_ind_proveedor
				,t200.f200_ind_empleado
				,t200.f200_ind_accionista
				,t200.f200_ind_otros
				,t200.f200_ind_interno
				,RTRIM(t200.f200_nombre_est) AS f200_nombre_est
				,t200.f200_fecha_nacimiento
				,t200.f200_id_ciiu
				,t200.f200_ind_estado
				,t200.f200_ind_no_domiciliado
				,t200.f200_ts
				FROM t200_mm_terceros t200
				) AS Tabla
				'
			IF @f_filters = ''
				BEGIN
                SET @query = @sql	+ ' ORDER BY ' + @paramOrderPag
                            + ' OFFSET ' + CONVERT(NVARCHAR(MAX),@skipReg) + ' ROWS'
                            + ' FETCH NEXT ' + CONVERT(NVARCHAR(MAX),@tamPag) +' ROWS ONLY'
                EXEC sp_executesql @query
				END
			ELSE
				BEGIN
                SET @query = @sql	+ ' WHERE ' + CONVERT(NVARCHAR(MAX),@f_filters)
                            + ' ORDER BY ' + @paramOrderPag
                            + ' OFFSET ' + CONVERT(NVARCHAR(MAX),@skipReg) + ' ROWS'
                            + ' FETCH NEXT ' + CONVERT(NVARCHAR(MAX),@tamPag) +' ROWS ONLY'
                EXEC sp_executesql @query
				END
			END	 					
	END 
END
	TRY  
BEGIN 
	CATCH
		SELECT 'Por favor verifique los filtros enviados.' AS 'alerta'
END CATCH
---
```




    ◦ Variables de Paginación
    DECLARE @numPag INT = {numPag} 
    DECLARE @tamPag INT = {tamPag} 
    DECLARE @paramOrderPag NVARCHAR(MAX) = 'f200_rowid' 
    DECLARE @skipReg INT = (@numPag-1) * @tamPag 
    DECLARE @pageLimitSize INT = 100; 
    DECLARE @f_filters NVARCHAR(MAX) = {Filters} 
    DECLARE @query NVARCHAR(MAX) 
    DECLARE @sql NVARCHAR(MAX)

#### V4 Ejecutar Consulta Dinamica
**Request URL**

    Tipo: GET
    URL: https://serviciosqa.siesacloud.com/api/connekta/v4/ejecutarconsulta?idCompania=1&descripcion=interfacesysoluciones_terceros_json_bd_formato_connekta

**Notas**:

La responsabilidad de la serializacion la tiene la base de datos y no el mocroservicio.

Se debe incluir en el select la Clausula **"FOR JSON PATH"** obligatoriamente para que el servidor le de el formato json. 

Tiene dos funcionalidades, se puede usar sin paginacion, como en el ejemplo que se muestra aqui que es una consulta directa al servidor, o para incluir paginacion es necesario definir variables como se definio en la API V3.1 Ver allí la "consulta ejemplo" con el manejo de variables, en caso de que el cliente requiera paginación.

Esta version permite tener "querys" anidados sin que se vea datos repetidos o cartesianos.

Aplica para SQL 2016 en adelante.

**Uso**:

Ejemplo sin paginación

{% include inline_image.html
file="API_V2_0016.png" alt="" %}

{% include inline_image.html
file="API_V2_0014.png" alt="" %}

Se debe incluir en el select la Clausula "FOR JSON PATH" para que el servidor le de el formato json.

Si no se pone esta clausula

Se presentaria el siguiente error al tratar de ejecutar el microservicio

{% include inline_image.html
file="API_V2_0015.png" alt="" %}

Esta version permite tener "querys" anidados sin que se vea datos repetidos o cartesianos.

Ejemplo
Simulando Items con Extensiones

{% include inline_image.html
file="API_V2_0017.png" alt="" %}

{% include inline_image.html
file="API_V2_0018.png" alt="" %}

Al ejecutar

{% include inline_image.html
file="API_V2_0019.png" alt="" %}

Se puede notar el árbol Item - extensiones

Formato del servicio de Connekta

{% include inline_image.html
file="API_V2_0020.png" alt="" %}

Notar que el servicio de Connekta siempre mostrara Codigo, mensaje y detalle

#### V4.0.1 Ejecutar Consulta Dinamica Cache

**Request URL**

    Tipo:GET
    URL: {base_url_qa}/api/connekta/v4.0.1/ejecutarconsulta?idCompania={idCompania}&descripcion=interfacesysoluciones_items&paginacion=numPag=1|tamPag=100

**Notas**:

Se extendio el API V4 Ejecutar Consulta Dinamica con el manejo del Cache, y la paginacion es requerida.

Es decir, se agrego a la versión 4 en la versión 4.0.1 la naturaleza del funcionamiento en cache, que consiste en que se hace el llamado a la base de datos en la página 1, y este llamado o la información es guardada en cache para que a partir de la página 2 la aplicación no vaya a la base de datos, sino que consulte la información en memoria (cache) dando el resultado mucho mas rápido y consumiendo menos recursos. 

El cache tiene dos vencimientos: El primero es cuando se envía la página 1, en ese momento, borra el cache y lo carga de nuevo desde la base de datos.

Y el segundo se maneja en una variable en los headers del uso del API llamado "Connekta-Cache-Time-Remaining" variable que maneja el tiempo que permanece la información en cache, cuando este tiempo expira se elimina la información del cache y se vuelve a leer y cargar en cache la información desde la base de datos.

En Connekta, en la documentación siempre se garantiza que inicie desde la página uno.

Se usa para consultas con muchos mas datos que la versión 4.0 ya que exige paginación y por que usa Cache.

Cuando se maneja cache en la APIs, la cantidad de registros se puede ampliar hasta 10.000 registros por pagina.

La respuesta en esta API desde la pagina dos debe mejorar mucho el desempeño.

**Uso**:

#### V4.1 Ejecutar Consulta Dinamica

**Request URL**

    Tipo: GET
    URL: https://serviciosqa.siesacloud.com/api/connekta/v4.1/ejecutarconsulta?idCompania=1&descripcion=interfacesysoluciones_items_json_universal

**Notas**:

Es igual a la versión API V4 pero sin la clasificación que hace Connekta, los datos se van con la convención universal del query completo. 

Se pueden añadir otras características como por ejemplo poner la cláusula Root().

Al igual que la versión de la API V4, para incluir paginación es necesario definir variables como se definió en la API V3.1 Ver allí la "consulta ejemplo" con el manejo de variables, en caso de que el cliente requiera paginación.


**Uso**:

{% include inline_image.html
file="API_V2_0021.png" alt="" %}

 Notar que al consumir se muestra sin la Codificación de Connekta, sale en formato universal

{% include inline_image.html
file="API_V2_0022.png" alt="" %}

Al agregar la clausula Root() en el Select y ejecutar el Microservicio

{% include inline_image.html
file="API_V2_0023.png" alt="" %}

El resultado es el siguiente:

{% include inline_image.html
file="API_V2_0024.png" alt="" %}

En el ejemplo se puso Nodo de Items

#### V4.1.1 Ejecutar Consulta Dinamica Cache
**Request URL**

    Tipo: GET
    URL: {base_url_qa}/api/connekta/v4.1.1/ejecutarconsulta?idCompania={idCompania}&descripcion=interfacesysoluciones_items&paginacion=numPag=1|tamPag=100

**Notas**:

Se extendio el API V4.1 Ejecutar Consulta Dinamica con el manejo del Cache, y la paginacion es requerida.

Es decir, se agrego a la versión 4.1 en la versión 4.1.1 la naturaleza del funcionamiento en cache, que consiste en que se hace el llamado a la base de datos en la página 1, y este llamado o la información es guardada en cache para que a partir de la página 2 la aplicación no vaya a la base de datos, sino que consulte la información en memoria (cache) dando el resultado mucho mas rápido y consumiendo menos recursos. 

El cache tiene dos vencimientos: El primero es cuando se envía la página 1, en ese momento, borra el cache y lo carga de nuevo desde la base de datos.

Y el segundo se maneja en una variable en los headers del uso del API llamado "Connekta-Cache-Time-Remaining" variable que maneja el tiempo que permanece la información en cache, cuando este tiempo expira se elimina la información del cache y se vuelve a leer y cargar en cache la información desde la base de datos.

En Connekta, en la documentación siempre se garantiza que inicie desde la página uno.

Se usa para consultas con muchos mas datos que la version 4.1 ya que exige paginación y por que usa Cache. Cuando se maneja cache en la APIs, la cantidad de registros se puede ampliar hasta 10.000 registros por pagina.

La respuesta en esta API desde la pagina dos debe mejorar mucho el desempeño. 

Todas las APIs que manejan Cache la paginación es obligatoria.

**Uso**:


#### V5 Ejecutar Consulta Dinamica


**Request URL**

    Tipo: POST
    URL: {base_url_qa}/api/connekta/v5/ejecutarconsulta?idCompania={idCompania}&idSistema=13

**Notas**:

Notar que el API V5 es de tipo POST, es diferente a las APIs Dinámicas anteriores. 

Todas las APIs anteriores de la Version V3 hasta la versión V4.1.1, tienen la caracteristica de que estan parametrizadas en Connekta. 
Para este caso si todo lo anterior no aplica, se debe validar esta API, aqui el sistema se "abre" un poco para permitir el manejo del "body", y se deja la responsabilidad en el interesado que este ejecutando la acción.

En el Body debe llegar una peticion de consulta "QrySql" el cual debe contener un query String encriptado de la consulta que se quiere realizar, esta codificación o encriptacion se debe realizar con una herramienta que le debemos proveer al cliente para que lo genere.
(Poner alusion a imagen del programa que se debe entregar minuto, Ver imagen ...) 

Aplica en Sistemas que son muy interactivos, son querys que se arman dinamicamente en un momento dado y no se sabe hasta ese momento como seria la consulta.
Esta API, se debe asociar a un sistema especifico en Connekta, este sistema especifico, manejara su propia conexion, a la base de datos que se desee. 

Lo que hace el API es tomar la consulta que viene encriptada, internamente la desencripta, y toma la conexion del sistema al que se asocio, y retorna la información solicitada en la consulta en el JSON de respuesta, (ver ejemplo imagen...) 

En el Body "QrySql" se carga la informacion dependiendo de las reglas de negocio que maneje en el cliente especifico. Funciona en clientes muy dinamicos.

**Uso**:


### **Interfaces**

#### V3 Interfaces Queries Por Sistema

**Request URL**

    Tipo: GET
    URL: {base_url_qa}/api/connekta/v3/interfacesqueriesporsistema?idCompania={idCompania}&IdSistema=1

**Notas**:

Es una API utilizada para los sistemas que se están desarrollando internamente, y está estrechamente relacionada con lo que denominamos "propiedades offline".
El objetivo es eliminar todas las dependencias de lo que existe en Connekta, trasladando toda la información a un archivo encriptado localmente, desde el cual se pueda acceder y realizar ciertas operaciones.

Esta API vincula visualmente lo que se ve en Connekta como un sistema y obtiene todas las interfaces generadas para dicho sistema. Un ejemplo gráfico de esto se puede ver en la imagen adjunta. Cada interfaz puede tener consultas (queries) asociadas, y a través de esta API es posible obtener toda la información de las interfaces, junto con sus queries. Un ejemplo gráfico de esto también se muestra en la imagen.

Con esta API, se puede escalar la información hacia sistemas externos que necesiten centralizarla dentro de Connekta. Este es solo uno de los componentes del mecanismo offline, y proporciona acceso a la información del sistema en sí, las interfaces asociadas y, dentro de ellas, los queries que maneja un sistema determinado en Connekta.


**Uso**:

<!--
### **Logs**

#### V3 Gestionar Log

#### V3.1 Gestionar Log
-->

### **Parametros**

#### V3 Parametros Por Sistema

**Request URL**

    Tipo: GET
    URL: {base_url_qa}/api/connekta/v3/parametrosporsistema?idCompania={idCompania}&idSistema=5&descripcionParametro

**Notas**:

Esta API está estrechamente relacionada con la API "V3 Interfaces Queries por Sistema", ya que permite obtener la información de un sistema en modo "offline".
Es similar a la API anterior, pero en este caso se recuperan los parámetros y conexiones configuradas en el sistema (ver imagen), así como los parámetros del Ecosistema asociado. 

Con esta API, junto con la "V3 Interfaces Queries por Sistema", se obtiene toda la información disponible en Connekta sobre un sistema, y se maneja en modo "offline", lo que permite reducir la cantidad de llamadas a Connekta. Este enfoque facilita la reutilización dentro de un sistema propio y se denomina desacoplamiento de la dependencia de los satélites.


**Uso**:

<!--

#### V3 Parametros Por Compañía


### **Token**

#### V3 Generar Token


## **SIESA** 

### **ERP**
#### MODULO CONECTIVIDAD
##### **V3 Consultas Estandar**
##### **V3 Ejecutar Consulta Estandar**
##### **V3 Conectores Estandar**
##### **V3 Conectores Estructura Estandar**
##### **V3 Conectores Generar Plano Estandar**
##### **V3 Conectores Importar Estandar**
#### APIS DINAMICAS
##### **V3 Conectores Dinamicos**
##### **V3 Conectores Estructura Dinamico**
##### **V3 Conectores Generar Plano Dinamico**
##### **V3 Conectores Generar Plano Impodatos Dinamico**
##### **V3 Conectores Importar Dinamico**
##### **V3.1 Conectores Importar Dinamico**
### **NOMINA WEB**
#### V3 Nomina Web
#### V3.1 Nomina Web


## **ZEUS**

### **SALUD**
#### MODULO CONECTIVIDAD
#### APIS DINAMICAS
-->