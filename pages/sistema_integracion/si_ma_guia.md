---
title: Connekta - Módulo de Administración
keywords: 
last_updated: Febrero 6, 2025
tags: #[getting_started]
#summary: "Inicio del Módulo de administración"
sidebar: sistema_integracion_sidebar
permalink: si_ma_guia.html
folder: sistema_integracion
---

## **Descripción:**

Se describe a continuación como se gestionan los usuarios y permisos en el Sistema de Integración de Siesa, con alcance para el Módulo de Conectividad y el Módulo de APIs Dinámicas con aplicación en los roles de usuario tipo “Admin” y “Cliente”. 

## **Ingreso al Gestor de Integraciones** ##

Para ingresar al Gestor de Integraciones es necesario disponer y usar un enlace (Link) similar al siguiente para su compañía; uno para QA (Ambiente de pruebas) y otro para CORE (Ambiente de Producción), en esta guía nos basaremos solo en la parte de QA, pero es igual para CORE, la diferencia entre QA y CORE es que en QA se trabaja en ambiente de pruebas y en CORE se trabaja en ambiente productivo en el ERP de Siesa.  

### URL para QA: ### 

https://integradorqa.siesacloud.com/login/[nombrecompañia]  

Donde [nombrecompañia] se reemplaza con el nombre asignado a su compañía, para el ejemplo usaremos la siguiente:  

https://integradorqa.siesacloud.com/login/generictransfer [demo](https://integradorqa.siesacloud.com/login/generictransfer) 

Al ingresar a este enlace en un navegador web se debe mostrar algo similar a la siguiente imagen: 

{% include inline_image.html
file="MA_1.png" alt="" %}

Dependiendo de lo adquirido por la compañía donde aparece la etiqueta “Gestor de Integraciones” podría aparecer también la etiqueta “Modulo de Conectividad” en vez de la etiqueta anterior. 

Para ingresar debe disponer de un usuario (por lo general correo electrónico) 

y una contraseña valida, credenciales asignadas por el administrador del Gestor de Integraciones, al ingresar las credenciales validas, se muestra el siguiente formulario:

{% include inline_image.html
file="MA_2.png" alt="" %}

Al iniciar se muestran diferentes datos estadísticos del Gestor de integraciones. 

En esta guía nos centraremos en la Opción Administración, y dentro de esta en las opciones Usuarios y Permisos.  

Al presionar la opción “Administración”, la primera opción en la parte superior a la izquierda nos aparece el siguiente formulario 

## **Administración** ##

{% include inline_image.html
file="MA_3.png" alt="" %}

En esta guía inicialmente solo describiremos el funcionamiento del manejo de las opciones Usuarios y Permisos 

## **Usuarios** ##

Para gestionar usuarios debemos dar clic sobre la palabra “gestionar” de la opción Usuarios en el formulario de administración o imagen anterior, se nos debe mostrar un formulario similar al siguiente: 

{% include inline_image.html
file="MA_4.png" alt="" %}

Se pueden ver los usuarios que hay creados para esta compañía, el formulario por defecto los muestra en páginas de tamaño diez con un encabezado y algunos iconos y otros elementos que ayudan con la operación. A continuación, se explicarán los componentes y funcionamiento del formulario. 

Descripción de los iconos que se presentan en el formulario anterior. 

{% include inline_image.html
file="MA_5.png" alt="" %}

Explicación de las columnas 

{% include inline_image.html
file="MA_6.png" alt="" %}

{% include inline_image.html
file="MA_7.png" alt="" %}
Aquí se puede mencionar que la lista que se muestra de usuarios se puede ordenar por la columna que se desee, presionando con el Mouse sobre la columna que se desee ordenar, o permite filtrar la información, usando el icono de embudo con el Mouse en la columna y llenando la información necesaria para aplicar el filtro.

A continuación, se explicará en detalle algunas de las opciones: 

### Crear ###

Al presionar el icono  Crear, se muestra el siguiente formulario, para ingresar la información del usuario: 

{% include inline_image.html
file="MA_8.png" alt="" %}

Aquí se debe ingresar la información solicitada, Nombre, Apellido, Teléfono (opcional), Correo electrónico, Seleccionar el Rol y seleccionar la compañía del usuario, y al final presionar el botón guardar. 

{% include inline_image.html
file="MA_9.png" alt="" %}

En la selección del rol aparecen los roles que la persona que está gestionando puede asignar al usuario que está creando. 

{% include inline_image.html
file="MA_10.png" alt="" %}

Ejemplo de la creación de un usuario con rol Cliente 

{% include inline_image.html
file="MA_11.png" alt="" %}

Al guardar el usuario aparece este mensaje y se envía un correo electrónico con las credenciales. 

{% include inline_image.html
file="MA_12.png" alt="" %}

Al revisar el correo del usuario, llega uno marcado con remitente “Notificaciones connekta” llegan las credenciales (usuario y clave), si no llega a la bandeja de entrada, puede estar en "Correos no deseados", Ver en la imagen anterior como llega el mensaje, notar un botón para ir directamente al sistema, si se presiona el botón “Iniciar Sesión” lo envía directamente al sistema de integración para que inicie sesión.

{% include inline_image.html
file="MA_13.png" alt="" %}

Aquí se inicia sesión, y en el primer ingreso se solicita el cambio de contraseña como se muestra a continuación: 

{% include inline_image.html
file="MA_14.png" alt="" %}

### Token ###

Esta información de Token (key y token) son las “llaves” necesarias para el uso o consumo de las API, conectores o consultas. 

Al presionar el icono  Token, se muestra el siguiente formulario, para asignar el key y el token al usuario existente: 


{% include inline_image.html
file="MA_15.png" alt="" %}

Al presionar el botón “Generar” se generan el “Key” y el “Token” 


{% include inline_image.html
file="MA_16.png" alt="" %}

Si se quiere que el Token varie en el tiempo se puede usar la caja de chequeo de ¿Expira? Y la cantidad de días que se desee la variación. Se pueden usar los iconos de copia de la parte derecha de cada caja de texto para copiar los valores tanto del Key como del Token para su uso en el consumo de las API de Conectores y consultas. 

### Migrar ###

Al presionar el icono  Migrar a producción, se muestra el siguiente dialogo  

{% include inline_image.html
file="MA_17.png" alt="" %}

Si presiona el botón que se desee. 

Es necesario advertir, que se habla de migrar cuando estamos en el ambiente de QA y se requiere crear el usuario en CORE o producción. Es de anotar que el usuario migra a CORE sin los permisos que tenga en QA, es necesario renovar los permisos en el ambiente de CORE. 

### Editar ###

Al presionar el icono  Editar, se muestra el siguiente formulario 

{% include inline_image.html
file="MA_18.png" alt="" %}

Se permite editar la información del usuario en los campos Nombre, Apellido y Teléfono. 

### Eliminar ###

Al presionar el icono  Eliminar, se muestra el siguiente dialogo 

{% include inline_image.html
file="MA_19.png" alt="" %}
Se selecciona la opción que se desee. 

## **Permisos** ##

Son los permisos que se asignan a los usuarios de los diferentes Servicios ofrecidos. 

Para gestionar permisos debemos dar clic sobre la palabra “gestionar” de la opción Permisos en el formulario de Administración, se nos debe mostrar un formulario similar al siguiente: 

{% include inline_image.html
file="MA_20.png" alt="" %}

{% include inline_image.html
file="MA_21.png" alt="" %}

Cada registro representa un usuario y que permisos tiene asignados, o usando la herramienta se le pueden asignar. A continuación, veremos el detalle por cada columna.

### Microservicios ###

En esta columna se manejan todos los microservicios que hay disponibles para uso desde el sistema de integración 

{% include inline_image.html
file="MA_22.png" alt="" %}

Para dar un permiso sobre un microservicio, se debe desplegar la caja de selección y marcar la caja de chequeo del microservicio que se desee asignar. Si se desea seleccionar todos los microservicios basta marcar la caja de chequeo que aparece frente a la lupa. En el caso de la imagen, los marcados en azul están asignados al usuario seleccionado. 

### Conectores Estándar ###

Los conectores estándar son conectores predefinidos que se asocian con el Módulo de conectividad. Y sirven para importar información al ERP de Siesa desde otros orígenes de información, información manual o de otros sistemas. 

 

En esta columna se manejan todos los conectores estándar disponibles para uso 

{% include inline_image.html
file="MA_23.png" alt="" %}

Para dar un permiso sobre un conector estándar, se debe desplegar la caja de selección y marcar la caja de chequeo del conector estándar que se desee asignar. Si se desea seleccionar todos los conectores estándar basta marcar la caja de chequeo que aparece frente a la lupa. En el caso de la imagen, los marcados en azul están asignados al usuario seleccionado. 

### Conectores Dinámicos ###

Este tipo de conector no se maneja en el Módulo de Conectividad. Si se requiere su manejo, se debe adquirir el módulo de APIs dinámicas con el Área Comercial. 

Los conectores dinámicos son los conectores que se construyen con el apoyo del equipo de soporte de Generic Transfer y están asociados al módulo de APIs Dinámicas. Al ser Dinámicos, se pueden personalizar para las necesidades específicas, pudiendo fijar campos, haciendo su manejo más fácil en el desarrollo de soluciones. Por defecto el sistema no trae ningún conector dinámico, se pueden usar los que hayan creados en la plataforma Generic Transfer los cuales se pueden importar desde el Sistema de Integración, sino, estos se van construyendo en la plataforma de Generic Transfer y se van añadiendo al sistema de integración. 

{% include inline_image.html
file="MA_24.png" alt="" %}

Para dar un permiso sobre un conector dinámico, se debe desplegar la caja de selección y marcar la caja de chequeo del conector dinámico que se desee asignar. Si se desea seleccionar todos los conectores dinámicos basta marcar la caja de chequeo que aparece frente a la lupa. En el caso de la imagen, los marcados en azul están asignados al usuario seleccionado. 

### Consultas Estándar ###

Las consultas estándar son consultas predefinidas que se asocian con el Módulo de conectividad. Sirven para obtener información del ERP de Siesa. 

 

En esta columna se manejan todas las consultas estándar disponibles para uso, ver imagen a continuación 

{% include inline_image.html
file="MA_25.png" alt="" %}

Para dar un permiso sobre una consulta estándar, se debe desplegar la caja de selección y marcar la caja de chequeo de la consulta estándar que se desee asignar. Si se desea seleccionar todas las consultas estándar basta marcar la caja de chequeo que aparece frente a la lupa. En el caso de la imagen, las marcadas en azul están asignadas al usuario seleccionado. 

### Consultas Dinámicas ###

Este tipo de consulta no se maneja en el Módulo de Conectividad. Si se requiere su manejo, se debe adquirir el módulo de APIs dinámicas con el Área Comercial. 

Las consultas dinámicas son las consultas que se construyen con el conocimiento que se tenga de la base de datos del ERP de Siesa. Al ser dinámicas se personalizan según las necesidades que se tengan, por defecto el sistema de integraciones no trae ninguna consulta dinámica. A medida que se van construyendo se van añadiendo al Sistema de integración. 

{% include inline_image.html
file="MA_26.png" alt="" %}

Para dar un permiso sobre una consulta dinámica, se debe desplegar la caja de selección y marcar la caja de chequeo de la consulta dinámica que se desee asignar. Si se desea seleccionar todas las consultas dinámicas basta marcar la caja de chequeo que aparece frente a la lupa. En el caso de la imagen, las marcadas en azul están asignadas al usuario seleccionado. 

### Restricciones ###

El módulo de restricciones se aplica únicamente a la extracción de información, ya sea del módulo de conectividad o de APIs dinámicas. Su objetivo principal es evitar la ejecución de sentencias maliciosas durante la extracción de información. Por defecto, se maneja la prevención de SQL Injection, lo que impide que un usuario realice comandos como Insert, Update, Delete, Drop Table, etc., en sus consultas. Sin embargo, este módulo va más allá, permitiendo que los usuarios definan sus propias reglas de negocio para limitar el acceso o las vistas a la información. 

  

Si el cliente necesita implementar restricciones adicionales, como impedir que ciertos usuarios vean la información de una tabla específica, se pueden definir cláusulas exactas dentro de las consultas. Es posible limitar aspectos como esquemas, columnas, tablas, etc. Es importante mencionar que este sistema de restricciones aún se está perfeccionando. Por ello, se debe validar exhaustivamente que la restricción funcione correctamente antes de otorgar permisos a los usuarios sobre las consultas, asegurando así el funcionamiento deseado. 

 

Las restricciones se van construyendo en el mismo sistema de integraciones en la opción del menú de administración: “Restricciones” 

{% include inline_image.html
file="MA_27.png" alt="" %}

Para dar un permiso sobre una restricción, se debe desplegar la caja de selección y marcar la caja de chequeo de la restricción que se desee asignar. Si se desea seleccionar todas las restricciones basta marcar la caja de chequeo que aparece frente a la lupa. En el caso de la imagen, las marcadas en azul están asignadas al usuario seleccionado. 

## **Glosario de términos informáticos** ##



{% include inline_image.html
file="MA_28.png" alt="" %}
