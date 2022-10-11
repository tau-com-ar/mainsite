---
layout: post
title:  "Orquestando con Kubernetes"
date:   2022-10-11 08:07:32 -0300
categories: general kubernetes
---
# Orquestando Contenedores

A medida que las empresas empezaron a adoptar el uso de contenedores (a menudo como parte de arquitecturas modernas y nativas en cloud), la simplicidad del contenedor individual comenzó a chocar con la complejidad de gestionar cientos (incluso miles) de contenedores en un sistema distribuido.

Para solucionar este reto, surgió la orquestación de contenedores como una forma de gestionar grandes volúmenes de contenedores en su ciclo de vida, lo que incluye:

* Suministro
* Redundancia
* Supervisión de estado
* Asignación de recursos
* Escalado y equilibrio de carga
* Movimiento entre hosts físicos
     
Aunque se crearon muchas plataformas de orquestación de contenedores (como Apache Mesos, Nomad y Docker Swarm) para ayudar a solucionar este reto, Kubernetes, un proyecto de código abierto introducido por Google en 2014, se convirtió rápidamente en la plataforma de orquestación de contenedores más popular, y es la que la mayoría de la industria ha estandarizado.

Kubernetes permite a los desarrolladores y operadores declarar un estado deseado de su entorno de contenedores global mediante archivos YAML. A continuación, Kubernetes hace todo el trabajo duro para establecer y mantener ese estado, con actividades que incluyen el despliegue de un número especificado de instancias de una determinada aplicación o carga de trabajo, el reinicio de esa aplicación si falla, el equilibrio de carga, el escalado automático, despliegues de tiempo de inactividad cero, etc.

Un clúster de Kubernetes es un conjunto de máquinas que ejecutan aplicaciones en contenedores. Se puede dividir en dos partes: los equipos en el plano de control (denominados masters) y los equipos en el plano de trabajo (denominados workers). 

La interfaz de programación de aplicaciones o API de Kubernetes es el frontend del plano de control de este sistema, y se encarga de la interacción de los usuarios con el clúster de Kubernetes. El servidor de la API determina si una solicitud es válida y se encarga de procesarla.
La API es la interfaz que se utiliza para gestionar, crear y configurar los clústeres de la plataforma. Es la forma que utilizan los usuarios, los elementos externos y las partes del clúster para comunicarse entre sí.

# Cómo funciona Kubernetes

Su funcionamiento depende del estado definido y del real. Los objetos de Kubernetes representan el estado de un clúster, y comunican a la plataforma cuál es la apariencia de la carga de trabajo que usted desea.

Una vez que se crean y se definen, Kubernetes se encarga de garantizar su permanencia.

Los controladores gestionan de forma activa el estado de los objetos y realizan los cambios necesarios para que el clúster pase de su estado actual al deseado.

Los desarrolladores o los administradores de sistemas indican el estado definido a través de archivos YAML o JSON que envían a la API de Kubernetes. La plataforma utiliza un controlador para analizar la diferencia entre el nuevo estado definido y el real en el clúster.

El estado deseado define las aplicaciones o las cargas de trabajo que deben ejecutarse, las imágenes en contenedores que se utilizan, los recursos que deben estar disponibles y demás ajustes.

Los datos de configuración y del estado del clúster se alojan en la etcd, una base de datos distribuida de almacenamiento de clave-valor que posee tolerancia a los fallos y está diseñada para ser la principal fuente de información del clúster.

Entonces Kubernetes gestionará el clúster de forma automática para que coincida con él. Por lo general, los controladores se encargan de ello enviando mensajes al servidor de la API para generar los cambios necesarios, y algunos vienen integrados en ciertos recursos de Kubernetes.

Para darse una idea de cómo trabaja la plataforma, imagínese que implementa una aplicación con un estado deseado de "tres"; es decir, deberían ejecutarse tres réplicas de la aplicación.

Si uno de los contenedores falla, el conjunto de réplicas de Kubernetes notará que solo funcionan dos de ellas y agregará una más para lograr el estado deseado.

Los conjuntos de réplicas son un tipo de controlador que garantiza la ejecución de un número determinado de pods en todo momento.

Las implementaciones de Kubernetes son el método preferido para gestionarlos y brindan actualizaciones declarativas a los pods, para que usted no tenga que administrarlos de forma manual.

También puede utilizar la escalabilidad automática en Kubernetes para ajustar sus servicios en función de las necesidades de los usuarios. Al especificar el estado deseado de una aplicación o un servicio, tiene la posibilidad de indicar al controlador que deje pods adicionales disponibles en caso de que aumente la demanda.

Por ejemplo, durante los períodos ajetreados, el estado deseado de la aplicación puede aumentar a diez réplicas, en lugar de las tres habituales.

En Tau contamos con años de experiencia trabajando con Kubernetes y microservicios en general. [Contáctenos](https://tau.com.ar/contacto/) para conocer cEómo podemos ayudarlo a aprovechar los numerosos beneficios de esta tecnología.
