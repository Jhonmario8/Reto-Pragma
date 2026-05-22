# 🍽️ Reto-Pragma: Ecosistema de Microservicios para Plazoleta de Comidas

Repositorio principal (monorepo) de la solución **Reto-Pragma**. Este repositorio funciona como orquestador central que agrupa y gestiona 4 microservicios independientes, cada uno representando un dominio específico dentro de la arquitectura del proyecto.

El sistema está diseñado bajo los principios de la **Arquitectura Hexagonal (Clean Architecture)**, utilizando **Java 17** y **Spring Boot 3**, y soporta persistencia políglota integrando bases de datos relacionales (**MySQL**) y NoSQL (**MongoDB**).

## Tabla de Contenidos

- [Descripción General](#descripción-general)
- [Arquitectura y Tecnologías](#arquitectura-y-tecnologías)
- [Microservicios (Submódulos)](#microservicios-submódulos)
- [Cómo Clonar Este Repositorio](#cómo-clonar-este-repositorio)
- [Instalación y Configuración Global](#instalación-y-configuración-global)
- [Actualización de Submódulos](#actualización-de-submódulos)
- [Autor y Contacto](#autor-y-contacto)

---

## Descripción General

**Reto-Pragma** es el repositorio padre que centraliza el desarrollo de una solución integral para la gestión de restaurantes, menús y pedidos. Utiliza submódulos de Git para permitir el desarrollo y despliegue independiente de cada componente, manteniendo una gestión de versiones unificada.

El ecosistema garantiza la validación de usuarios mediante seguridad JWT, orquestación de pedidos, envío de notificaciones asíncronas a clientes y un registro inmutable de trazabilidad para métricas de eficiencia.

## Arquitectura y Tecnologías

El proyecto implementa un enfoque de microservicios con las siguientes tecnologías clave:

* **Lenguaje y Framework:** Java 17, Spring Boot 3.3.5.
* **Diseño:** Arquitectura Hexagonal (Puertos y Adaptadores).
* **Comunicación:** Spring Cloud OpenFeign (comunicación HTTP síncrona).
* **Seguridad:** JSON Web Tokens (JWT) para autenticación y autorización basada en roles.
* **Persistencia Políglota:**
    * **MySQL 8:** Utilizado por los microservicios de Usuarios y Plazoleta para garantizar la integridad transaccional y relacional del negocio.
    * **MongoDB:** Utilizado por el microservicio de Trazabilidad para el registro ágil y escalable de logs y auditoría orientada a documentos.
* **Integraciones Externas:** API de Twilio para el envío de notificaciones vía SMS/WhatsApp.
* **Mapeo y Utilidades:** MapStruct, Lombok.
* **Construcción:** Gradle.

## Microservicios (Submódulos)

Este repositorio vincula los siguientes proyectos a través de submódulos de Git:

1. **[user-service](URL_DEL_REPO_USERS)**: Microservicio encargado de la gestión de roles, autenticación JWT y creación de usuarios (Propietarios, Empleados, Clientes). *[Persistencia: MySQL]*
2. **[plazoleta-service](URL_DEL_REPO_PLAZOLETA)**: Núcleo del negocio. Gestiona la creación de restaurantes, platos y la orquestación del ciclo de vida de los pedidos. *[Persistencia: MySQL]*
3. **[messaging-service](URL_DEL_REPO_MESSAGING)**: Microservicio adaptador que integra el SDK de Twilio para enviar alertas al usuario cuando su pedido está listo. *[Sin persistencia]*
4. **[traceability-service](URL_DEL_REPO_TRACEABILITY)**: Microservicio de auditoría que registra los tiempos de inicio, fin y eficiencia de cada pedido y empleado. *[Persistencia: MongoDB]*

## Cómo Clonar Este Repositorio

Para descargar el proyecto completo, incluyendo el código fuente de todos los microservicios (submódulos), ejecuta el siguiente comando:

```bash
git clone --recursive [https://github.com/Jhonmario8/Reto-Pragma.git](https://github.com/Jhonmario8/Reto-Pragma.git)