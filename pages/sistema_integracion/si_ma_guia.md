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





