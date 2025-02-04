---
title: Módulo de Administración
keywords: 
last_updated: Diciembre 18, 2024
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