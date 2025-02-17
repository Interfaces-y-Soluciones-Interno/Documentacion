---
title: Connekta - Módulo de Conectividad
keywords: 
last_updated: Febrero 6, 2025
tags: #[getting_started]
#summary: "Inicio del Modulo de conectividad"
sidebar: sistema_integracion_sidebar
permalink: si_mc_guia.html
folder: sistema_integracion
---

## **Descripción:** ##

Un módulo de conectividad es una herramienta que facilita la conexión entre diferentes sistemas que utilizas en tu empresa. Imagina que es como un "puente" que une tus sistemas con otros sistemas externos (como tu sistema de ventas con el sistema de inventario de un proveedor).

¿Cómo Funciona?

Consultas Estándar: Ofrece una serie de consultas predefinidas que puedes usar para obtener o enviar información entre sistemas. Por ejemplo, una consulta puede ayudarte a traer datos de ventas de tu sistema a tu sistema de contabilidad.

Conectores: Incluye herramientas especiales llamadas conectores que permiten que tus sistemas hablen entre sí sin complicaciones.

Autogestión: Te permite configurar y ajustar cómo quieres que se realicen estas conexiones sin necesidad de ayuda técnica constante. Puedes hacer cambios o ajustes cuando lo necesites.

Soporte y Guías: Incluye instrucciones y ayuda para que puedas entender cómo usar el módulo y resolver cualquier problema que surja.

Beneficios

Ahorra Tiempo: Las conexiones están listas para usar, por lo que puedes empezar a integrarlas rápidamente.

El Módulo de Conectividad provisto por el Gestor de Integraciones de Siesa, actualmente tiene 42 consultas y 39 conectores prediseñados en forma estándar y documenta toda la información que maneja (ver Documentador).

Las consultas más usadas son:

- Bodegas 
- Clientes 
- Terceros 
- Conceptos nomina 
- Ítems 
- Proveedores 
- Servicios 
- Terceros 

Los conectores más usados son: 

- Ítems 
- Documentos contables
- Clientes
- Proveedores
- Terceros 
- Pedido de Venta comercial
- Factura de Venta   

Si se requiere realizar consultas o conectores dinámicos (personalizados), es necesario que adquiera el **Módulo de Apis dinámicas**, aquí es necesario dirigirse al área comercial.  

En Siesa actualmente se dispone de un sistema Gestor de Integraciones (antes conocido como Connekta), el cual incluye el Módulo de Conectividad.

## **Ingreso al Gestor de Integraciones** 


Para ingresar al Gestor de Integraciones es necesario disponer y usar un enlace (Link) similar al siguiente para su compañía; uno para QA (Ambiente de pruebas) y otro para CORE (Ambiente de Producción), en esta guía nos basaremos solo en la parte de QA, pero es igual para CORE, la diferencia entre QA y CORE es que en QA se trabaja en ambiente de pruebas y en CORE se trabaja en ambiente productivo en el ERP de Siesa.  

### **URL para QA:**

https://integradorqa.siesacloud.com/login/[nombrecompañia]

Donde [nombrecompañia] se reemplaza con el nombre asignado a su compañía, para el ejemplo usaremos la siguiente: 

https://integradorqa.siesacloud.com/login/ecommerce [Ecommerce](https://integradorqa.siesacloud.com/login/ecommerce)

Al ingresar a este enlace en un navegador web se debe mostrar algo similar a la siguiente imagen:


{% include inline_image.html
file="1_GestorIntegraciones.png" alt="" %}


Para ingresar debe disponer de un usuario (por lo general correo electrónico) 

y una contraseña valida, credenciales asignadas por el administrador del Gestor de Integraciones, al ingresar las credenciales validas, se muestra el siguiente formulario: 

{% include inline_image.html
file="MC_2.png" alt="" %}

Al iniciar se muestran diferentes datos estadísticos del Gestor de integraciones.  

Al presionar la opción de **Integraciones** al inicio en el panel izquierdo, aparece lo siguiente: 

{% include inline_image.html
file="MC_3.png" alt="" %}

Todos los ecosistemas con los que interactúa el Gestor de integraciones  

Aquí aparece un panel con las opciones de **Sistemas** y **Parámetros.**  

Al presionar el botón de **Parámetros**, para el caso del módulo de conectividad, se presenta el siguiente formulario donde se deben configurar todas las variables necesarias para que el módulo de conectividad pueda interactuar con el ERP de Siesa. Por lo regular esto se configura en compañía del Integrador asignado. Estos parámetros se deben tener tanto para el ambiente de pruebas como para el de producción, es decir, todas las credenciales y accesos requeridos en el ERP de Siesa y para la Base de datos de Siesa son necesarios para poder trabajar en el ambiente de pruebas y en el ambiente Real, en este documento solo se muestra para el ambiente de pruebas. 

{% include inline_image.html
file="MC_4.png" alt="" %}

Estas variables son: 

{% include inline_image.html
file="MC_5.png" alt="" %}



Aquí es necesario anotar, que también el cliente debe suministrar al personal encargado de Siesa un ‘ConexionString’ de la base de datos del ERP que se esté configurando, local o nube, con las respectivas credenciales validas, dependiendo el tipo de conexión al ERP de Siesa que tenga el Cliente. Si el Cliente es Cloud esta información la aporta directamente el área de Siesa IT. Si esto no se realiza, el sistema de Consultas estándar no funcionaría correctamente. 
 

En un "ConexionString”, se maneja la dirección IP o URL del servidor de SQL, el nombre de la base de datos y las credenciales de acceso en el servidor de base de datos SQL. Las credenciales de autenticación en el SQL deben tener solo acceso de lectura a las bases de datos. 

 

Ejemplos de ‘‘ConexionString” 

**Local:**  

Pruebas: 

Data Source=192.168.0.1;Initial Catalog=UnoEE_Pruebas;User ID=connekta;Password=C0nn3ktA* 

Real: 

Data Source=192.168.0.1;Initial Catalog=UnoEE;User ID=connekta;Password=C0nn3ktA*

**Nube:** 

Data Source=ec2-3-233-106-192.compute-1.amazonaws.com;Initial Catalog=UnoEE_Pruebas;User ID=Pedrouser1;Password=Pedropass$82$% 
 



Continuando en el formulario de Ecosistemas después de haber visto los parámetros: 
 
{% include inline_image.html
file="MC_3.png" alt="" %}

Luego al presionar el botón de **Sistemas** se nos presentan todos los módulos que el Gestor de integraciones nos provee, en la siguiente imagen podemos observar específicamente, **el Módulo de conectividad**, que es lo que se explica en esta guía  

 
 {% include inline_image.html
file="MC_6.png" alt="" %}
 

### **Ingreso al Documentador** 

 

Al presionar el botón Documentador (de la imagen anterior), se nos presentan dos opciones: **Conectores** y **Consultas** 

 
{% include inline_image.html
file="MC_7.png" alt="" %}
 

### **Conectores** 

 

Los conectores son especificaciones realizadas por Siesa para facilitar la importación de información, información manual u obtenida de otros Sistemas para ser importada al ERP de Siesa. 

 

Al elegir la opción Conectores del Documentador 

{% include inline_image.html
file="MC_8.png" alt="" %}



Se muestran todos los conectores estándar que se pueden usar para su compañía, aparece un listado ordenado por páginas. 

En la parte Izquierda de cada registro de los conectores aparecen dos iconos con un funcionamiento especial, ver en la imagen siguiente los iconos resaltados en amarillo.  

 
{% include inline_image.html
file="MC_9.png" alt="" %}
 

 

El icono con forma de ojo permite ver el anexo: 

 

 {% include inline_image.html
file="MC_10.png" alt="" %}

 

Este anexo lo que permite es ver las diferentes Secciones del conector, una sección en un conector es una parte de este que agrupa información relacionada, en el siguiente ejemplo hay una sección para el manejo de Terceros, es de anotar que todos los conectores manejados en Siesa tienen por defecto una sección inicial y una sección final adicional a sus secciones funcionales. 

 
 {% include inline_image.html
file="MC_11.png" alt="" %}
 

Para seleccionar una sección específica del conector use el selector “Seleccione una sección” 

  {% include inline_image.html
file="MC_12.png" alt="" %}

Para este ejemplo del conector de Terceros, se tienen tres secciones, Inicial, Terceros y Final 

 

Al seleccionar la sección Terceros nos aparecen todos los campos que se manejan en esta sección especifica, agrupados de a 10 ítems por página, en este caso tiene 35 Ítems y por tanto 35 campos en esta sección: 

   {% include inline_image.html
file="MC_13.png" alt="" %}

 

Este detalle de los campos en una sección de un conector se usa para validar la información de los diferentes campos a usar en el conector, se le puede dar un uso como “Diccionario de datos”, ya que describe el tipo, si es obligatorio o no, y el tamaño del campo, la observación también se usa en la validación y los posibles valores que debe llevar el campo. 

 

El siguiente icono, símbolos mayor y menor, permite ver la guía del conector. 

 
   {% include inline_image.html
file="MC_14.png" alt="" %}
 

Al seleccionar el icono “Ver guía” aparece el siguiente formulario: 

 {% include inline_image.html
file="MC_15.png" alt="" %}

Este formulario permite ver información asociada del conector. Y con esta información se puede dar manejo al API de los conectores. Esto lo veremos más adelante en este documento. Ver “Como se utilizan las APIs ...” 

 



### **Consultas** 

 

Las consultas estándar son especificaciones creadas por Siesa para facilitar la consulta de alguna información del ERP de Siesa, las consultas se nombran al final con la información que devolverá al usarse. 

 
{% include inline_image.html
file="MC_16.png" alt="" %}
 

Al presionar consultas, se muestran todas las consultas estándar que se pueden usar para su compañía. En el formulario el listado de las consultas se ordena por páginas, en el caso de la imagen anterior, se tienen 10 registros de consultas por página. 

Al igual que en los conectores nos aparecen dos iconos en la parte izquierda de cada registro. 


{% include inline_image.html
file="MC_17.png" alt="" %}
 

Y sirven para lo mismo, pero en este caso aplica para las consultas, veamos el detalle: 

 

El icono con forma de ojo permite ver el anexo: 

 
{% include inline_image.html
file="MC_18.png" alt="" %}
 

Veamos algo más, para aplicar un Filtro a los registros de la lista que se muestra, se puede aplicar tanto en Conectores como en consultas, en la parte derecha de cada registro, hay un icono en forma de embudo, este permite hacer un filtro a los registros, como se muestra a continuación: 

 
{% include inline_image.html
file="MC_19.png" alt="" %}
 

En este caso aplicamos un filtro para buscar la consulta “Api_v2_Terceros” 

 

Veamos al presionar el icono de Ver Anexo de la consulta API_v2_Terceros nos aparece lo siguiente: 

 
{% include inline_image.html
file="MC_20.png" alt="" %}
 

Aparecen todos los campos que maneja la consulta, a diferencia de los conectores, aquí aparece toda la lista de los campos de la consulta en la misma página (en la imagen no se muestran todos los registros, es necesario navegar hacia abajo usando el Scroll para irlos viendo).  Describe también en forma de “Diccionario de datos” los campos que se mostraran en la consulta. 

 

Notar al inicio de la página que se especifica que solo se puede usar la información de la columna “Campo” para los filtros de la consulta. 

 

El siguiente icono, símbolos mayor y menor, permite ver la guía de la consulta. 

 
{% include inline_image.html
file="MC_21.png" alt="" %}
 

 {% include inline_image.html
file="MC_22.png" alt="" %}

 

 

 

Al igual que en los conectores este formulario permite ver información asociada a la consulta. Y con esta información se puede dar manejo al API de las consultas. Esto lo veremos la próxima sección de este documento. Ver “Como se utilizan las APIs ...” a continuación. 

 
 
 

## **Como se utilizan las APIs y ejemplos de uso en Postman** 

 

Postman: es una herramienta utilizada para probar APIs, permitiendo a los desarrolladores enviar peticiones a servicios web y ver las respuestas. (https://www.postman.com) 

 

### **Obtención de información en el documentador para usar las Apis** 

 

Para obtener la información para el uso de las APIs tanto para consultas estándar como para conectores estándar, debemos en el documentador al ingresar a los conectores o consultas usar el icono “Ver Guía” en la parte izquierda de cada registro. Como se vio en las secciones anteriores. 

 

 

### **Uso para las consultas estándar** 

 

Para el ejemplo usaremos la consulta API_v2_Terceros 

 
{% include inline_image.html
file="MC_23.png" alt="" %}
 

Al presionar el icono “Ver Guía” aparece el siguiente formulario:  

 
{% include inline_image.html
file="MC_24.png" alt="" %}
 

Este formulario tiene varios componentes útiles, los explicaremos a continuación. 

Tiene cuatro bandas de información. 

La primera banda contiene: 

**- Type**: (tipo) es GET ósea que es para obtener o consultar información.  

La segunda banda contiene: 

**- Base URL**: permite seleccionar una opción 

 
{% include inline_image.html
file="MC_25.png" alt="" %}
 

**Local**: cuando el cliente tiene la plataforma Local y se instala el componente local, se menciona más adelante en este documento. 

**QA**: cuando está instalado en nube (también podría aparecer Core, en este caso es porque se está en ambiente QA) 

 

Al seleccionar una de las opciones se puede notar como cambia el dato en Request URL 

 

**- Request URL**, se podría definir que este es el “Endpoint” a usar para el uso del API. Esta información se puede copiar para llevarla directamente al Postman usando el enlace (Copiar URL) 

La tercera banda contiene: 

Los Headers o encabezados para la petición que se hará, estas son las llaves de seguridad asignados a cada cliente 

- **Connikey** 

- **Connitoken** 

Frente a cada uno se presenta un enlace para copiar el contenido en cada caso (Copiar) 

La cuarta banda contiene: 

Los **Params** o parámetros que se usan en la petición 

**idCompania**: 7501

**descripcion**: API_v2_Terceros

**paginacion**: numPag=1\|tamPag=100

**parametros**: {parametros} 



**Significado de cada parámetro**: (se omiten tildes en algunas palabras para ser congruentes con lo que se presenta en el formulario) 

 

**Idcompañia**: Código asignado al cliente en el Sistema 

**descripcion**: Descripción de la consulta a usar 

**paginacion**:  Definición de que página se consultara y tamaño de los registros por página. (esto es obligatorio en las consultas) 

**parametros**:  Datos adicionales para filtrar la información de la consulta usando los campos. 

 

 

### **Uso en Postman** ###

En una colección creada en postman, para este caso Test_documentacion, se crea una nueva petición. (Add request) 

 
{% include inline_image.html
file="MC_26.png" alt="" %}
 

En Postman nos aparece un “New Request” como en la siguiente imagen, nos debemos ubicar donde dice “Enter URL o Paste text” (se resalta en amarillo) aquí es donde se copiará la información que se obtiene de la Guía” también es conocido como el “EndPoint”. 

 {% include inline_image.html
file="MC_27.png" alt="" %}

En la Guía vamos a Copiar URL después de haber seleccionado la Base URL 

 
{% include inline_image.html
file="MC_28.png" alt="" %}
 

Después de presionar el botón Copiar URL nos ubicamos de nuevo en Postman y pegamos la información obtenida, quedando lo siguiente en Postman: 

 
{% include inline_image.html
file="MC_29.png" alt="" %}
 

Notar que se crean todos los “Query Params” que se traen en la URL, pero faltaría agregar los Headers, en Postman nos ubicamos en la pestaña Headers y creamos las dos variables para Connikey y Connitoken y los valores para estos los obtenemos de la Guía, copiando cada valor.  

 

Imagen parcial de la Guía copiando la información de Connikey y Connitoken 

 

 {% include inline_image.html
file="MC_30.png" alt="" %}

 

Quedando lo siguiente en Postman después de la copia de cada llave: 

 
{% include inline_image.html
file="MC_31.png" alt="" %}
 

Notar que se crearon dos variables en la columna Key y al frente la columna Value que ya tiene los valores obtenidos en la copia en la Guía y se muestran en forma parcial.  

 

Con esto ya se podría probar el “Endpoint”. Presionando el botón “Send” en Postman. 

 

Revisar la próxima imagen, después de dar “Send” se puede notar que se realizó la consulta en forma satisfactoria. Donde se obtienen los datos de la consulta. 


{% include inline_image.html
file="MC_32.png" alt="" %}

Despues de presionar el Botón “Send” muestra el mensaje “Transacción exitosa”, y debajo trae el “detalle” significa que todo está correcto y devolvió la información de la consulta en el objeto “Table”. 

 

En este punto ya se puede guardar la petición en Postman en la respectiva colección.  Para nuestro caso renombramos donde dice New Request, en la parte superior por Terceros y en la colección ya nos queda un EndPoint de Terceros en los Get. 


 
{% include inline_image.html
file="MC_33.png" alt="" %}
 

En el uso de las consultas, la paginación es obligatoria. 

Para paginación usar lo siguiente: 

numPag=1\|tamPag=100 

 
Para incluir filtros en la consulta se usa el parámetro llamado (**parametros**), para filtrar se usa la columna **campo**, ver sección Consultas antes en este documento.  

Los filtros funcionan en forma similar cómo funciona la cláusula Where en SQL, donde se puede filtrar por un solo campo o por varios campos usando operadores relacionales entre ellos. 

 

Para filtros con manejo de Texto se debe manejar la comilla simple ' dos veces al inicio y al final de la palabra, ejemplo: f284_descripcion = ''Genérico'' 

 

Para Los campos numéricos usados en los filtros se pueden usar como parámetros el valor numérico sin comillas. 

 

Algunos de los símbolos de comparación entre campos que se pueden usar son: 

  

= 

LIKE 

AND 

OR 

  

 

 

Ejemplo de Filtro usando dos comillas simples al principio y al final del contenido del filtro 

 
{% include inline_image.html
file="MC_34.png" alt="" %}
 

Aquí se puso como filtro en parametros el valor f200_nit =''1144182829'' (ojo no es comilla doble, sino dos comillas sencillas en cada lado para el filtro de texto) 

 

Un ejemplo de filtro combinando dos campos en forma relacional. 

 

  
{% include inline_image.html
file="MC_35.png" alt="" %}

 

Aquí se relacionaron dos campos uno texto y el otro numérico, notar que la consulta devuelve los datos cumpliendo con el filtro incluido. 

 
 
{% include inline_image.html
file="MC_36.png" alt="" %}
 

 

#### Errores en el uso del API para consultas 

 

El sistema tiene control de errores cuando hay algo que no se ha manejado bien y muestra mensajes alusivos a lo que pudo pasar, veamos un ejemplo, en la consulta anterior, se ha dejado un error en los parámetros donde se filtra, el sistema mostrara un error como lo que sigue: 

 

 {% include inline_image.html
file="MC_37.png" alt="" %}

 

En este ejemplo se usó dos puntos en vez del signo igual en el filtro por indicador de proveedor (f200_id_ciiu = ''0010'' and f200_ind_proveedor : 1), se puede notar que la Transacción fue exitosa, esto significa que la consulta fue enviada, pero luego se identificó el error en el filtro que se envió como se muestra en la “alerta”, resaltado en amarillo. 

 

### **Uso para los conectores estándar**

 

Para esto usaremos el conector API_v1_Terceros 

 
 {% include inline_image.html
file="MC_38.png" alt="" %}

 

Al presionar el icono de “Ver Guía” similar como en las consultas, nos presenta el siguiente formulario, dividido también en cuatro bandas. 

 {% include inline_image.html
file="MC_39.png" alt="" %}

Las dos primeras bandas son similares a las de la consulta, con la diferencia en el Type (tipo) del API aquí es POST, con esto indica que es para llevar información hacia el ERP, recordar que con los conectores se permite importar información el ERP de Siesa, lo demás es igual que en la sección anterior. (ver la sección anterior, la explicación de estas dos bandas) 

 

La banda tres contiene los “Params” que en este caso son: 

**idCompania**: 7501  

**idDocumento**: 150484 

**nombreDocumento**: API_v1_Terceros 

 

Significado: 

 

**idCompania**: identificador de la compañía al interior del sistema

**idDocumento**: número interno del documento en el sistema 

**nombreDocumento**: Descripción del conector en el sistema 

 

Y la banda cuatro de la guía contiene el “Body”, este es un ejemplo de la estructura del conector a usar en formato Json y sin datos, pero como ejemplo completo de cómo se debe usar el conector. Si damos ***copiar Body***, nos copia algo como lo siguiente en este caso: 


``` json
{
  "Inicial": [
    {
      "F_CIA": ""
    }
  ],
  "Terceros": [
    {
      "F_CIA": "",
      "F_ACTUALIZA_REG": "",
      "F200_ID": "",
      "F200_NIT": "",
      "F200_DV_NIT": "",
      "F200_ID_TIPO_IDENT": "",
      "F200_IND_TIPO_TERCERO": "",
      "F200_RAZON_SOCIAL": "",
      "F200_APELLIDO1": "",
      "F200_APELLIDO2": "",
      "F200_NOMBRES": "",
      "F200_NOMBRE_EST": "",
      "F200_IND_CLIENTE": "",
      "F200_IND_PROVEEDOR": "",
      "F200_IND_EMPLEADO": "",
      "F200_IND_ACCIONISTA": "",
      "F200_IND_OTROS": "",
      "F200_IND_INTERNO": "",
      "F015_CONTACTO": "",
      "F015_DIRECCION1": "",
      "F015_DIRECCION2": "",
      "F015_DIRECCION3": "",
      "F015_ID_PAIS": "",
      "F015_ID_DEPTO": "",
      "F015_ID_CIUDAD": "",
      "F015_ID_BARRIO": "",
      "F015_TELEFONO": "",
      "F015_FAX": "",
      "F015_COD_POSTAL": "",
      "F015_EMAIL": "",
      "F200_FECHA_NACIMIENTO": "",
      "F200_ID_CIIU": "",
      "F200_IND_NO_DOMICILIADO": "",
      "F200_IND_ESTADO": "",
      "F015_CELULAR": ""
    }
  ],
  "Final": [
    {
      "F_CIA": ""
    }
  ]
}
```


Se puede notar que es la estructura “vacía” en formato Json del conector y de cómo debe enviarse el “body”  luego en la petición. Veamos el ejemplo del “consumo” del API en Postman. Creamos una nueva petición (Add request) en Postman, procurando que sea POST, luego nos ubicamos en la Guía del Gestor y seleccionamos la Base URL y **Copiar URL** 

 {% include inline_image.html
file="MC_40.png" alt="" %}

Vamos a Postman y copiamos la información donde corresponde 

 
{% include inline_image.html
file="MC_41.png" alt="" %}
 

Notar que es un “New Request”, tipo POST, y al pegar el “EndPoint” que se copió desde la guía, automáticamente se crean los “Query params” IdCompania, IdDocumento y nombreDocumento. La configuración del API aún no está completa. 

Luego ubicados en Postman se deben crear los Headers para Connikey y Connitoken y se copia la información de valor para cada uno desde la Guía, como se realizó en la sección anterior debe quedar algo como lo siguiente: 

 
{% include inline_image.html
file="MC_42.png" alt="" %}
 

 

 

Luego se debe llenar la estructura copiada del body con los datos que se llevaran al ERP de Siesa. Y se copia esta estructura Json “llena” en la parte del Postman donde se maneja el Body a continuación se muestra la estructura Json ejemplo con datos, en este caso, solo llenamos los datos requeridos y algunos los dejamos vacíos, en su caso pueden llenar todo lo que requieran en su compañía, esta información debe ser copiada en la parte del Body de la petición en el Postman, como se muestra en la siguiente imagen en Postman.  

 
``` json
{
	"Inicial": [
		{
			"F_CIA": "1"
		}
	],
	"Terceros": [
		{
			"F_CIA": "1",
			"F_ACTUALIZA_REG": "1",
			"F200_ID": "9898989898",
			"F200_NIT": "9898989898",
			"F200_DV_NIT": "",
			"F200_ID_TIPO_IDENT": "C",
			"F200_IND_TIPO_TERCERO": "2",
			"F200_RAZON_SOCIAL": "EJEMPLO DE TERCERO",
			"F200_APELLIDO1": "",
			"F200_APELLIDO2": "",
			"F200_NOMBRES": "",
			"F200_NOMBRE_EST": "EJEMPLO DE TERCERO",
			"F200_IND_CLIENTE": "0",
			"F200_IND_PROVEEDOR": "0",
			"F200_IND_EMPLEADO": "0",
			"F200_IND_ACCIONISTA": "0",
			"F200_IND_OTROS": "0",
			"F200_IND_INTERNO": "0",
			"F015_CONTACTO": "",
			"F015_DIRECCION1": "",
			"F015_DIRECCION2": "",
			"F015_DIRECCION3": "",
			"F015_ID_PAIS": "",
			"F015_ID_DEPTO": "",
			"F015_ID_CIUDAD": "",
			"F015_ID_BARRIO": "",
			"F015_TELEFONO": "",
			"F015_FAX": "",
			"F015_COD_POSTAL": "",
			"F015_EMAIL": "",
			"F200_FECHA_NACIMIENTO": "20230602",
			"F200_ID_CIIU": "0010",
			"F200_IND_NO_DOMICILIADO": "0",
			"F200_IND_ESTADO": "1",
			"F015_CELULAR": ""
		}
	],
	"Final": [
		{
			"F_CIA": "1"
		}
	]
}
```
 

Al copiar en Postman el Json anterior en la sección Body 

 
{% include inline_image.html
file="MC_43.png" alt="" %}
 

Con todo esto ya se puede realizar el “consumo”. Se presiona el Botón “Send” y si todo está bien la transacción debe ser exitosa. 

 {% include inline_image.html
file="MC_44.png" alt="" %}

Al presionar el botón ”Send” se ejecuta el API, y en la imagen se puede notar que la importación fue exitosa, esto significa que el conector funciono bien y la información fue importada al ERP de Siesa en forma exitosa.  

 

#### Errores en el uso del API para conectores 

 

El sistema tiene control de errores cuando hay algo que no se ha manejado bien y muestra mensajes alusivos a lo que pudo pasar, veamos un ejemplo, en el conector anterior no se pasa el dato de la compañía en la sección inicial del conector, el sistema mostrara un error como sigue: 

 
{% include inline_image.html
file="MC_45.png" alt="" %}
 

Básicamente muestra el detalle del error como lo mostraría en ERP de Siesa 

 

## **Información complementaria** 

### **¿Qué es el componente local?** 

  

Es una aplicación de Siesa que se instala en los servidores locales del cliente, para facilitar la comunicación con el Gestor de Integraciones. Esta aplicación permite sincronizar la información del Gestor de Integraciones en la Nube con el servidor en forma local. Es necesario tener acceso a Internet desde el Servidor donde se instala el componente local para facilitar la comunicación. Luego de sincronizar las APIs del Gestor de Integraciones funcionan localmente. 

 

El componente local solo se instala en los Clientes que manejan el ERP de Siesa localmente, para los clientes de nube de Siesa no les aplica el componente local. 

 

Cuando se instala el componente local, se instala un manejador de las APIs en Forma Local, el sitio local que se genera maneja lo que se denomina Swagger. 

 

Las APIs de consultas y conectores estándar funcionan en la misma forma que se explicó antes en este documento, la única diferencia es que en el EndPoint es necesario actualizar la ruta por una ruta local del servidor donde haya quedado instalado el componente local. 

 

 

## **Glosario de términos informáticos** 

 
{% include inline_image.html
file="MC_46.png" alt="" %}


