# Implementación de Controles DLP (Data Loss Prevention)

## Objetivo

Implementar controles básicos de Prevención de Pérdida de Datos (DLP) para proteger la información sensible de la organización, reduciendo el riesgo de accesos no autorizados, filtraciones y pérdida de información.

---

## Clasificación de Datos

La información se clasifica según su nivel de sensibilidad:

| Clasificación | Descripción                                        | Ejemplos                                               |
| ------------- | -------------------------------------------------- | ------------------------------------------------------ |
| Público       | Información disponible para cualquier persona.     | Sitio web institucional, comunicados oficiales         |
| Interno       | Información para uso exclusivo de la organización. | Procedimientos internos, documentación administrativa  |
| Sensible      | Información crítica o confidencial.                | Datos personales, credenciales, información financiera |

---

## Control de Acceso

Se aplica el principio de **menor privilegio**, otorgando únicamente los permisos necesarios para que cada usuario realice sus funciones.

### Medidas implementadas

* Uso de cuentas individuales.
* Restricción de privilegios administrativos.
* Revisión periódica de permisos.
* Revocación de accesos cuando un usuario cambia de función o deja la organización.

---

## Monitoreo y Auditoría

Las actividades relacionadas con datos sensibles deben ser monitoreadas y registradas.

### Eventos supervisados

* Acceso a información sensible.
* Transferencia de archivos.
* Uso de dispositivos USB.
* Intentos fallidos de autenticación.

### Herramientas recomendadas

* Sistemas SIEM para correlación de eventos.
* Soluciones DLP para detección y bloqueo de fugas de información.
* Registros de auditoría de Windows.

---

## Implementación de Control DLP: Restricción de Dispositivos USB

Como medida preventiva contra la extracción no autorizada de información, se configuró Windows para impedir la lectura y escritura en dispositivos de almacenamiento extraíbles.

### Configuración aplicada

1. Ejecutar `gpedit.msc`.
2. Navegar a la siguiente ruta:

```text
Configuración del equipo
└── Plantillas administrativas
    └── Sistema
        └── Acceso de almacenamiento extraíble
```

3. Habilitar las siguientes políticas:

* **Discos extraíbles: denegar acceso de lectura**
* **Discos extraíbles: denegar acceso de escritura**

### Evidencia de configuración

**Política de denegación de lectura**

![Denegar Lectura](imagenes/usb-read-block.png)

**Política de denegación de escritura**

![Denegar Escritura](imagenes/usb-write-block.png)

### Resultado esperado

* Los usuarios no pueden leer archivos desde dispositivos USB.
* Los usuarios no pueden copiar archivos hacia dispositivos USB.
* Se reduce significativamente el riesgo de exfiltración de datos mediante medios físicos.

---

## Prevención de Filtraciones

Las siguientes medidas complementan la estrategia DLP:

* Cifrado de información sensible.
* Restricción de dispositivos externos.
* Control de transferencias de archivos.
* Monitoreo de actividades sospechosas.
* Gestión y respuesta ante incidentes.

---

## Concientización de Usuarios

La protección de la información también depende de los usuarios.

Se recomienda realizar capacitaciones periódicas sobre:

* Clasificación de la información.
* Buenas prácticas de seguridad.
* Riesgos de phishing.
* Manejo seguro de datos sensibles.
* Reporte de incidentes de seguridad.

---

## Conclusión

La implementación de controles DLP permite proteger la información sensible mediante controles preventivos y detectivos. La restricción de dispositivos USB constituye una medida efectiva para reducir el riesgo de fuga de información y fortalecer la seguridad de los activos de información de la organización.

---

## Evidencias

### Configuración de la Política de Lectura y Escritura

![Politica de Disco/USB Bloqueada](.png)

### Prueba de Restricción Aplicada

![Prueba de Restricción](.png)
