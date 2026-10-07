# Laboratorio 2 - Gestión de Servidores Web

## Caso: Dulce Hogar

Proyecto práctico grupal de la asignatura **Gestión de Servidores Web**, correspondiente a la Unidad 2: Servidores Web Propietario y Libre Distribución.

El proyecto consiste en implementar y documentar la infraestructura web local para la empresa ficticia **Dulce Hogar**, utilizando Ubuntu Server mediante WSL2, Apache, Virtual Host, Reverse Proxy y HTTPS mediante mkcert.

## Integrantes

| Integrante | Rol | Participación |
|---|---|---|
| Jefferson | Coordinador / Git | Organización, repositorio, integración y coordinación |
| Integrante 2 | Administrador de Servidor Base | Apache, estado, módulos y directorios |
| Integrante 3 | Administrador de Redes / Proxy | Virtual Host, Reverse Proxy y puertos |
| Integrante 4 | Administrador de Certificados SSL | mkcert, certificados y HTTPS |
| Integrante 5 | Administrador de Permisos OS | chown, chmod, www-data y confianza de CA |
| Integrante 6 | Documentador / QA | Capturas, documentación y pruebas |

> Los nombres de los integrantes y las actividades realizadas se actualizarán durante el desarrollo del proyecto.

## Estructura del proyecto

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

## Fases del proyecto

### Fase 1 - Dimensionamiento

Análisis de los recursos asignados al servidor, tráfico esperado, factor pico, escalabilidad y decisión entre servidor local o nube.

### Fase 2 - Apache

Instalación y configuración inicial de Apache en Ubuntu Server. Se verificará el estado del servicio, su inicio automático, los módulos necesarios y su funcionamiento.

### Fase 3 - Virtual Host + Reverse Proxy

Configuración del dominio local `dulcehogar.local`, Virtual Host y Reverse Proxy para conectar Apache con el servicio de la API mediante el puerto `9000`.

### Fase 4 - HTTPS

Configuración de HTTPS utilizando `mkcert`, generación del certificado local y configuración del Virtual Host SSL mediante el puerto `8900`.

## Dominio y puertos

- Dominio: `dulcehogar.local`
- HTTP: `80`
- API: `9000`
- HTTPS: `8900`

## Evidencias

Las capturas utilizadas en el proyecto corresponden al entorno propio del equipo y documentan las pruebas realizadas durante cada fase.

## Registro de participación

Cada integrante deberá realizar aportes al repositorio mediante commits identificables.

| Fase | Integrante | Actividad | Commit |
|---|---|---|---|
| Fase 1 | Pendiente | Dimensionamiento | Pendiente |
| Fase 2 | Pendiente | Apache | Pendiente |
| Fase 3 | Pendiente | Virtual Host / Reverse Proxy | Pendiente |
| Fase 4 | Pendiente | HTTPS / mkcert | Pendiente |
| Documentación | Pendiente | Informe y evidencias | Pendiente |

## Errores y soluciones

En esta sección se documentarán los errores encontrados durante la configuración y las soluciones aplicadas por el equipo.

## Tecnologías utilizadas

- Ubuntu Server LTS
- WSL2
- Apache2
- mkcert
- Git
- GitHub
- Reverse Proxy
- HTTPS

## Entrega

El repositorio será entregado mediante el enlace correspondiente en el campus virtual por el coordinador del equipo.