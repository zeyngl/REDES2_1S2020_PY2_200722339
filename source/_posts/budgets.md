---
title: Amazon Budgets
date: 2020-05-16 00:17:32
tags:
---


# Amazon Budgets

Presupuestos de AWS ofrece la posibilidad de definir presupuestos personalizados que alertan cuando los costos o el uso superan o se prevé que superen el importe presupuestado.

También se puede utilizar el servicio de Presupuestos de AWS para definir los objetivos de uso o cobertura de reservas y recibir alertas cuando el uso disminuya por debajo del limite definido. Es posible usar las alertas sobre reservas en los servicios Amazon EC2, Amazon RDS, Amazon Redshift, Amazon ElastiCache y Amazon Elasticsearch.


![alt_text](images/Copia-de5.png "image_tooltip")



## Mejores prácticas para controlar el acceso a los presupuestos de AWS

Para permitir que los usuarios de IAM creen presupuestos en la consola de AWS Billing and Cost Management, también debe permitir que los usuarios de IAM hagan lo siguiente:



*   Ver su información de facturación
*   Crear alarmas de Amazon CloudWatch
*   Crear notificaciones de Amazon Simple Notification Service (Amazon SNS)

También se puede crear presupuestos mediante programación utilizando la API de presupuestos. Al configurar el acceso a la API de presupuestos, se recomienda crear un usuario único de IAM para permitir el acceso programático. Esto ayuda a definir controles de acceso más precisos entre quién en su organización tiene acceso a la consola de Presupuestos y la API. Para dar acceso a consultas de múltiples usuarios de IAM a la API de Presupuestos, se recomienda crear un rol de IAM de acceso programático para cada uno de ellos.

