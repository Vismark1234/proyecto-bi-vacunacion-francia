# Git, GitHub y control de versiones

## Repositorio

El repositorio será público para que la fuente, el proceso y la documentación puedan revisarse. Los CSV mayores de 100 MB se almacenan mediante **Git LFS**; Git normal conserva punteros y LFS administra el contenido grande.

## Ramas

- `main`: versión estable y reproducible.
- `develop`: integración de trabajo cuando comiencen varios cambios relacionados.
- Ramas breves: `feature/etl-mensual`, `feature/modelo-sql`, `feature/tablero` o `docs/informe`.

Para un trabajo individual corto puede trabajarse directamente en ramas breves y fusionarlas en `main`. No se crearán ramas sin una necesidad real.

## Convención de commits

- `docs:` documentación y planificación.
- `data:` inventario, referencias o metadatos; nunca cambios silenciosos al bruto.
- `etl:` extracción, transformación y controles.
- `sql:` objetos y consultas de SQL Server.
- `bi:` modelo, DAX y tablero.
- `test:` validaciones.
- `fix:` correcciones verificadas.

Ejemplos: `docs: documentar alcance de la ruta 05` y `etl: agregar carga mensual idempotente`.

## Versiones y entregas

- `v0.1.0`: datos, alcance, arquitectura y planificación.
- `v0.2.0`: perfilamiento y ETL reproducible.
- `v0.3.0`: base SQL Server y análisis.
- `v0.4.0`: prototipo y prueba de usabilidad.
- `v1.0.0`: entrega final verificada.

Cada versión debe tener una nota que indique qué cambió, qué se validó y qué limitaciones permanecen.

## Archivos grandes

`.gitattributes` aplica LFS solo a `data/raw/**/*.csv`. Antes de cada publicación se comprobará:

```powershell
git lfs ls-files
git status
git diff --check
```

No se duplicarán los datos crudos dentro de resultados procesados. Si un archivo derivado es regenerable, se publicará el código y una muestra o resumen, no otra copia completa innecesaria.

## Información que nunca se publica

- contraseñas, tokens o cadenas de conexión;
- archivos `.env`;
- respaldos locales de SQL Server;
- datos personales o identificables;
- salidas temporales de Power BI, Python o editores.

