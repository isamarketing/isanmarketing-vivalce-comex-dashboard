# VIVALCE — Dashboard COMEX

Dashboard interactivo de monitoreo de importaciones para VIVALCE S.A.

## Acceso

El dashboard está publicado en GitHub Pages:
**https://[tu-usuario].github.io/vivalce-comex-dashboard/**

## Estructura

```
├── docs/                  # GitHub Pages (dashboard publicado)
│   └── index.html         # Dashboard interactivo
├── scripts/               # Automatización
│   ├── process_comex.py          # Script de procesamiento
│   └── dashboard_template.html   # Template HTML
├── data/                  # Archivos de datos (no versionados)
└── README.md
```

## Vistas del Dashboard

- **Overview** — Mercado total, market share VIVALCE (USD), evolución mensual, top importadores
- **COMEX 1 — Representadas** — ASK y SI GROUP: volumen, valor, precio, origen, productos
- **COMEX 2 — Competencia** — Ranking importadores con kg, FOB, precio, share, origen

## Actualización Mensual

### Requisitos
- Python 3.8+
- openpyxl (`pip install openpyxl`)

### Proceso

1. Obtener el Excel crudo del proveedor de datos de aduana

2. Ejecutar el script:
```bash
python scripts/process_comex.py \
  --input data/NUEVO_ARCHIVO.xlsx \
  --sheet "3909.40 Y2026" \
  --year 2026 \
  --previous data/ARCHIVO_AÑO_ANTERIOR.xlsx \
  --previous-sheet "3909 Y2025" \
  --previous-year 2025 \
  --output docs/index.html
```

3. Commit y push:
```bash
git add docs/index.html
git commit -m "Actualización COMEX - [MES] [AÑO]"
git push
```

4. El dashboard se actualiza automáticamente en GitHub Pages.

## Categorías

### Activas
- **Resinas Fenólicas** (3909.40) — ASK, SI GROUP

### Próximas
- Aditivos para Caucho (STRUKTOL)
- Caucho Nitrílico (NITRIFLEX)
- Cauchos Especiales (ZEON CHEMICALS)
- Aislantes Eléctricos (VON ROLL)
- Monómeros Acrílicos (ARKEMA)
- Polímeros EVA (PROQUITEC)
- Resinas Termoplásticas (BRASKEM)
- Compuestos de Purga (ASAHI, RAPID PURGE)

## Posiciones Arancelarias Monitoreadas

| Posición | Descripción |
|----------|-------------|
| 3909.40.11.000A | Resinas fenólicas liposolubles fenol-formaldehído |
| 3909.40.19.000L | Resinas fenólicas liposolubles otras |
| 3909.40.91.000D | Resinas fenólicas fenol-formaldehído |
| 3909.40.99.000P | Otras resinas fenólicas |
