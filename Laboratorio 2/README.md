# Laboratorio 2 - Gestión de Servidores Web

## Caso: Dulce Hogar — Repostería Artesanal

Proyecto práctico grupal de la asignatura **Gestión de Servidores Web**, correspondiente a la Unidad 2: Servidores Web Propietario y Libre Distribución, de la Universidad de Oriente (UNIVO).

El objetivo del proyecto es implementar, configurar y documentar una infraestructura web local para la empresa ficticia **Dulce Hogar**, utilizando Ubuntu Server mediante WSL2, Apache2, Virtual Host, Reverse Proxy y HTTPS mediante `mkcert`.

Durante el desarrollo se realizarán pruebas de funcionamiento, se documentarán los errores encontrados y se registrarán los aportes de cada integrante mediante commits en GitHub.

## 1. Integrantes y responsabilidades

| Integrante | Rol | Responsabilidades |
|---|---|---|
| Jefferson | Coordinador / Git | Organizar el equipo, administrar el repositorio, revisar los commits, coordinar la integración y consolidar el informe final. |
| Josué | Administrador del Servidor Base | Instalar Apache2, verificar el estado del servicio, habilitar los módulos necesarios y preparar los directorios. |
| Randal | Administrador de Redes / Proxy | Configurar el Virtual Host, el Reverse Proxy, los puertos y comprobar la comunicación con la API. |
| Juan | Administrador de Certificados SSL | Instalar y utilizar `mkcert`, generar los certificados locales y configurar HTTPS. |
| Brissvey | Administradora de Permisos del Sistema Operativo | Configurar propietarios y permisos con `chown` y `chmod`, verificar el acceso de `www-data` y establecer la confianza de la autoridad certificadora local. |
| Yessica | Documentación / QA | Recopilar capturas propias, documentar las pruebas, registrar errores y soluciones y apoyar en la preparación del informe final. |

### Organización del equipo

Cada integrante será responsable de apoyar en su fase asignada y documentar las actividades realizadas. Todos deberán participar en el repositorio mediante commits identificables y conocer el funcionamiento general del proyecto para prepararse para la defensa individual.

Las responsabilidades podrán complementarse durante la integración y las pruebas finales.

## 2. Objetivos del proyecto

- Analizar si los recursos asignados al servidor son adecuados para la carga esperada.
- Instalar y verificar el funcionamiento del servidor web Apache2.
- Configurar el dominio local `dulcehogar.local` mediante un Virtual Host.
- Configurar un Reverse Proxy para comunicar Apache con la API.
- Habilitar HTTPS mediante certificados locales generados con `mkcert`.
- Comprobar los permisos necesarios para el funcionamiento de los servicios.
- Documentar la configuración, las pruebas, los errores y las soluciones.
- Mantener un historial de trabajo colaborativo mediante Git y GitHub.

## 3. Entorno de trabajo

El proyecto se desarrollará en un entorno local utilizando las siguientes características:

| Recurso | Configuración |
|---|---|
| Sistema del servidor | Ubuntu Server LTS |
| Entorno de ejecución | WSL2 sobre Windows |
| CPU asignada | 2 vCPU |
| Memoria RAM | 4 GB |
| Almacenamiento | SSD de 40 GB |
| Servidor web | Apache2 |
| Tráfico habitual estimado | 500 visitas diarias |
| Tráfico máximo estimado | 3,000 visitas durante temporadas festivas |

Estas características se utilizarán como base para el análisis de dimensionamiento de la primera fase.

## 4. Estructura del proyecto

La carpeta principal del laboratorio tendrá la siguiente organización:

```text
Laboratorio 2/
├── README.md
├── informe-final.pdf
├── fase1-dimensionamiento.txt
├── fase2-apache.txt
├── fase3-virtualhost.txt
├── fase4-https.txt
├── config/
│   ├── dulcehogar.local.conf
│   ├── dulcehogar.local-ssl.conf
│   └── ports.conf
└── capturas/
    ├── fase2-apache-activo.png
    ├── fase3-curl-exitoso.png
    └── fase4-https-sin-advertencia.png
```

**Nota:** Los archivos de evidencias y el informe final se incorporarán cuando las pruebas y la documentación correspondientes estén terminadas. No se agregarán capturas ficticias ni resultados de pruebas que todavía no se hayan realizado.

## 5. Desarrollo por fases

### Fase 1. Dimensionamiento del servidor

Se analizarán los recursos asignados, el tráfico habitual y el tráfico máximo esperado para determinar si la infraestructura propuesta es adecuada.

Actividades principales:

- Evaluar la capacidad de procesamiento, memoria RAM y almacenamiento.
- Calcular el factor pico de tráfico.
- Analizar las posibilidades de escalabilidad vertical y horizontal.
- Identificar el primer recurso que se debería monitorear.
- Comparar las alternativas de infraestructura local y servicios en la nube.

**Archivo de documentación:** `fase1-dimensionamiento.txt`

### Fase 2. Instalación y configuración de Apache2

Se realizará la instalación y configuración inicial de Apache2 en Ubuntu Server.

Actividades principales:

- Instalar Apache2.
- Verificar el estado del servicio.
- Comprobar su inicio automático.
- Habilitar los módulos necesarios.
- Preparar los directorios de trabajo.
- Realizar pruebas para comprobar que el servidor funciona correctamente.

**Archivo de documentación:** `fase2-apache.txt`

**Evidencia prevista:** `capturas/fase2-apache-activo.png`

### Fase 3. Virtual Host y Reverse Proxy

Se configurará el dominio local `dulcehogar.local` y se establecerá la comunicación entre Apache y el servicio de la API mediante un Reverse Proxy.

Actividades principales:

- Crear y habilitar el Virtual Host.
- Configurar el dominio local.
- Preparar las reglas de proxy inverso.
- Utilizar el puerto `9000` para el servicio de la API.
- Verificar la comunicación mediante pruebas con `curl`.

**Archivo de configuración:** `config/dulcehogar.local.conf`

**Archivo de documentación:** `fase3-virtualhost.txt`

**Evidencia prevista:** `capturas/fase3-curl-exitoso.png`

### Fase 4. Configuración de HTTPS

Se configurará una conexión HTTPS local utilizando `mkcert` para generar los certificados necesarios.

Actividades principales:

- Instalar y preparar `mkcert`.
- Generar el certificado local para el dominio.
- Configurar el Virtual Host SSL.
- Configurar el uso del puerto `8900` para HTTPS.
- Establecer la confianza de la autoridad certificadora local cuando corresponda.
- Comprobar la conexión HTTPS y documentar los resultados.

**Archivos de configuración:**
- `config/dulcehogar.local-ssl.conf`
- `config/ports.conf`

**Archivo de documentación:** `fase4-https.txt`

**Evidencia prevista:** `capturas/fase4-https-sin-advertencia.png`

## 6. Dominio y puertos utilizados

| Elemento | Valor | Función |
|---|---|---|
| Dominio local | `dulcehogar.local` | Nombre local utilizado para acceder al sitio. |
| HTTP | `80` | Acceso web sin cifrado. |
| API | `9000` | Puerto del servicio de la API al que se dirigirá el Reverse Proxy. |
| HTTPS | `8900` | Puerto destinado a las pruebas de acceso web cifrado. |

Los puertos y las reglas definitivas se verificarán durante la configuración y las pruebas de cada fase.

## 7. Evidencias y pruebas

Las evidencias se guardarán en la carpeta `capturas/` y deberán corresponder al entorno de trabajo del equipo.

Se recopilarán, según corresponda:

- Capturas que demuestren que Apache2 está activo.
- Pruebas de acceso al dominio y de comunicación con la API.
- Pruebas de conexión HTTPS.
- Evidencias de los errores encontrados y las soluciones aplicadas, cuando sean relevantes.

Cada captura deberá mostrar información suficiente para identificar la prueba realizada. Las evidencias se agregarán después de ejecutar las comprobaciones correspondientes.

## 8. Registro de participación y commits

Para mantener la trazabilidad del trabajo, se registrarán las actividades desarrolladas y los commits asociados.

| Fase o actividad | Responsable principal | Actividad | Commit |
|---|---|---|---|
| Coordinación y repositorio | Jefferson | Creación del repositorio, estructura inicial y documentación del proyecto. | `b42a0f8`, `d776928` |
| Fase 1 | Jefferson y equipo | Dimensionamiento y análisis de infraestructura. | Por registrar |
| Fase 2 | Josué | Instalación y configuración de Apache2. | 5845163 |
| Fase 3 | Randal | Virtual Host, Reverse Proxy y pruebas de comunicación. | Por registrar |
| Fase 4 | Juan | Certificados locales y configuración HTTPS. | Por registrar |
| Permisos del sistema | Brissvey | Propietarios, permisos y comprobaciones de acceso. | Por registrar |
| Documentación y pruebas | Yessica | Capturas, registro de pruebas e informe final. | Por registrar |

Los responsables indicados son los encargados principales; esto no excluye la colaboración de los demás integrantes. Los commits se actualizarán con sus identificadores reales conforme avance el proyecto.

## 9. Registro de errores y soluciones

En esta sección se documentarán los problemas encontrados durante la instalación, configuración e integración de los servicios.

Para cada incidencia se procurará registrar:

- **Error encontrado:** descripción del problema.
- **Causa identificada:** explicación de la causa, si se pudo determinar.
- **Solución aplicada:** cambios o comandos utilizados para resolverlo.
- **Prueba de verificación:** comprobación realizada después de aplicar la solución.
- **Responsable:** integrante que atendió la incidencia.

Este registro permitirá explicar las decisiones técnicas durante la defensa del proyecto.

## 10. Tecnologías y herramientas utilizadas

- Ubuntu Server LTS.
- WSL2.
- Apache2.
- Virtual Host.
- Reverse Proxy.
- `mkcert`.
- HTTPS.
- Git.
- GitHub.
- `curl`.
- Terminal de Linux y PowerShell de Windows.

## 11. Repositorio del proyecto

**Repositorio oficial de GitHub:**

https://github.com/JeffersonUU7/gsw-practico-unidad2-equipo05

El repositorio contendrá los archivos de documentación, las configuraciones, las evidencias y el informe final del laboratorio.

Los cambios se incorporarán mediante commits identificables para facilitar el seguimiento de la participación de cada integrante.

## 12. Entrega final

La entrega se realizará mediante el enlace del repositorio de GitHub correspondiente, siguiendo las indicaciones del docente y del campus virtual.

Antes de entregar, el equipo verificará que:

- Las cuatro fases estén documentadas.
- Los archivos de configuración correspondan a los cambios realizados.
- Las evidencias sean auténticas y estén organizadas.
- El informe final esté incorporado.
- Los aportes de los integrantes estén registrados.
- Las pruebas de HTTP, Reverse Proxy y HTTPS estén documentadas.
- Todos los integrantes estén preparados para explicar el funcionamiento general del proyecto.
### Administración de permisos del sistema operativo (Brissvey)ø

- Se creó el directorio de práctica `/var/www/dulcehogar.local`.
- Se asignó la propiedad al usuario y grupo `www-data` mediante `chown`.
- Se establecieron permisos `755` para el directorio y `644` para el archivo `index.html` 
mediante `chmod`.
- Se verificó la propiedad y los permisos con `ls -ld` y `ls -l`.
- Se comprobó el acceso de lectura del usuario `www-data` al archivo web.

**Nota:** Las pruebas se realizaron en una máquina virtual local de Ubuntu. Falta validar los 
mismos cambios en el servidor compartido del equipo y coordinar la configuración de confianza 
de la CA.

