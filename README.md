# TBMS 2026 - Sistema de evaluación y seguimiento

Este repositorio contiene el código del formulario digital de evaluación TBMS 2026.

## Archivos

- `Code.gs`: backend en Google Apps Script.
- `formulario.html`: interfaz web del formulario.

## Estructura esperada de la hoja `Organizaciones`

| Columna | Campo |
|---|---|
| A | Organización |
| B | RUT Organización |
| C | Barrio |
| D | Tipología |
| E | UT Asignada (opcional) |
| F | Concejalía Asignada (opcional) |

Si la columna E está vacía, el sistema calcula la UT según la tipología.

## Hojas generadas por el sistema

- `Evaluaciones`: registro individual por evaluación.
- `Seguimiento`: consolidación por organización/proyecto.
- `Dashboard`: resumen de estado general.
- `Informe Organización`: informe consultable por organización mediante lista desplegable.

## Validaciones principales

- Campos obligatorios.
- Bloqueo del envío mientras se registra la evaluación.
- Modal de envío en curso.
- Validación de unidad técnica según tipología.
- Bloqueo de duplicados por organización/RUT + Unidad Técnica Evaluador/a.
- Adjudicabilidad automática: ADJUDICABLE si el promedio final es igual o superior a 75 y están las 3 evaluaciones requeridas.

## Cómo usar con GitHub

Este código puede versionarse en GitHub. Para sincronizar con Apps Script se recomienda usar `clasp`.

Comandos base:

```bash
npm install -g @google/clasp
clasp login
clasp clone <SCRIPT_ID>
# copiar Code.gs y formulario.html al proyecto local
clasp push
```

## Menú en Google Sheets

Al abrir la planilla aparecerá el menú `TBMS 2026`, con opciones para:

- Actualizar seguimiento
- Actualizar dashboard
- Actualizar informe por organización
- Actualizar todo
