---
title: NetFlow
date: 2020-05-15 20:52:30
tags:
---

# NetFlow

NetFlow es un protocolo de red creado por Cisco que recoge el tráfico de red IP a medida que fluye dentro o fuera de una interfaz. Los datos de flujo se analizan para crear una imagen del flujo y el volumen del tráfico de la red, por eso el nombre de: NetFlow.

Los profesionales de TI utilizan el protocolo NetFlow como un analizador de tráfico de red para determinar su punto de origen, destino, volumen y rutas en la red. Antes de NetFlow, los ingenieros y administradores de redes usaban el Protocolo simple de administración de redes (SNMP) para el análisis y monitoreo del tráfico de la red.

Si bien SNMP fue eficaz para la supervisión de la red y la planificación de la capacidad, no proporcionó información detallada sobre el uso del ancho de banda. NetFlow ahora forma parte del estándar del Grupo de trabajo de ingeniería de Internet (IETF) como eXport de información de flujo de protocolo de Internet (IPFIX, que se basa en la implementación de la versión 9 de NetFlow), y el protocolo es ampliamente implementado por los proveedores de equipos de red.

¿Cómo funciona NetFlow?

NetFlow sigue un proceso simple de recopilación, clasificación y análisis de datos. Los componentes principales incluyen:

Flujo IP

Un flujo de IP consta de un grupo de paquetes que contienen los mismos atributos de paquete de IP. A medida que un paquete se reenvía dentro de un enrutador o conmutador, se examina un conjunto de atributos, incluida la dirección de origen IP, la dirección de destino IP, el puerto de origen, el puerto de destino, el tipo de protocolo de capa 3, la clase de servicio y la interfaz de enrutador o conmutador.


![alt_text](images/Copia-de0.png "image_tooltip")


NetFlow Cache

El caché de NetFlow es una base de datos de información condensada donde los datos se almacenan una vez que se han examinado los paquetes.



![alt_text](images/Copia-de1.png "image_tooltip")


Interfaz de línea de comando

La interfaz de línea de comandos (CLI) es uno de los dos métodos para acceder a los datos de NetFlow. Proporciona una vista inmediata del tráfico de su red y es útil para la resolución de problemas.



![alt_text](images/Copia-de2.png "image_tooltip")


NetFlow Collector

La segunda opción para acceder a los datos de NetFlow es exportar los datos a un recopilador de NetFlow, que es un servidor de informes que recopila y procesa la información de tráfico para que sea fácil de analizar. Estos colectores NetFlow se dividen en dos categorías: colectores basados ​​en hardware y colectores basados ​​en software, siendo las soluciones de software más comunes que los dispositivos de hardware.




![alt_text](images/Copia-de3.png "image_tooltip")

