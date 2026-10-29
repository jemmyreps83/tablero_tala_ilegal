# Tablero de tala y comercio ilegal de madera — Estudio Regional 2024

Tablero interactivo y autocontenido (`index.html`) con los resultados del índice (TIi) y porcentaje (TI%) de tala y comercio ilegal de madera en rollo: **Estudio Regional 2024** (Ucayali, Madre de Dios y Loreto) y **medición nacional 2024** (diez departamentos), OSINFOR. Logo oficial del OSINFOR (`scripts/assets/logo_osinfor.svg`).

## Pestañas
| Grupo | Pestaña | Contenido |
|---|---|---|
| Regional | Resumen | KPI (DT, Oe, FNC, TIi, TI%), mapa con selector de indicador (incluye ENA / oferta movilizada) y alcance (TH + otros / solo TH), ficha, TI% por departamento, demanda vs. oferta efectiva, demanda según estudio (censo regional vs. muestra nacional), lectura comparada |
| Regional | Balance por modalidad | Flujo no controlado por modalidad (divergente), ENA / oferta movilizada por modalidad (Tablas 5, 13, 21), tabla completa de las Tablas 7, 15 y 23 con clasificación |
| Regional | Oferta, demanda y ENA | Composición por modalidad (% o m³r), participación departamental, detalle por modalidad |
| Nacional | Medición nacional | 7 KPI nacionales, mapa de 10 departamentos (demanda, oferta GTF, ENA, saldo demanda − oferta, % madera aserrada, factor de expansión), ficha, participación departamental, oferta vs. demanda por modalidad, balance nacional (Tabla 15), serie TI% 2017–2024, equivalencias del flujo no controlado (pt, S/, US$, árboles, ha, camiones) |
| Nacional | Especies y productos | 20 principales especies (GTF), especies con ENA, madera rolliza vs. aserrada por departamento |
| Ambos | Cobertura y diseño | Censo regional (directorio, resultado de visita), diseño muestral nacional, factores de expansión, calidad de la estimación |
| Ambos | Metodología | Fórmulas, clasificación, nomenclatura entre estudios (Oe/Oea), comparabilidad, siglas |

Cada gráfico tiene tooltip y vista de tabla. Modo claro/oscuro. Formato numérico: punto decimal y coma de miles.

## Regenerar
```
cd scripts
python build_data.py      # lee los .xlsx de la carpeta "Estudio Regional 2024" -> data/tala_regional_2024.json
python build_tablero.py   # ensambla index.html (assets/template.html + datos + cartografía)
```
`build_data.py` imprime un control de consistencia: los totales de la Base Acumulada (formato largo) deben coincidir con el Anexo 16.

## Publicación en GitHub Pages
Subir `index.html` a un repositorio (p. ej. `goodguysinsight/tablero_tala_ilegal`) y activar **Settings → Pages → Deploy from a branch → main / (root)**.

## Fuentes
- Documento Metodológico Estudio Regional Consolidado 2024 (v.02, 12.12.25): Tablas 1–24, Anexos 10–18.
- Base Acumulada Estudio Regional 2024 (v.03, 13.12.25): composición por modalidad.
- Informe nacional: OSINFOR (2025), *Medición del índice y porcentaje de tala y comercio ilegal de madera en el Perú, 2024* (PDF). Tablas 2, 3, 7, 8, 9, 11, 14 y 15, Figura 2 y sección 9, transcritas en `build_data.py` con controles de suma contra los totales publicados.
- Cartografía: RENLIM (SDOT–PCM), referencial.

## Notas
- El estudio regional es un censo: no corresponden intervalos de confianza; la calidad depende de errores no muestrales.
- La serie nacional se muestra como contexto; no es comparable punto a punto con el estudio regional (diseño muestral y ámbito de diez departamentos).
- Nomenclatura: el informe nacional llama Oe al volumen GTF y Oea a GTF − ENA; el tablero usa la nomenclatura regional (oferta movilizada y oferta efectiva).
- El informe nacional no publica índices por departamento; el saldo demanda − oferta por departamento incluye flujos interregionales y no equivale a tala ilegal departamental.
- El informe publica TI% nacional 54.8%; con las cifras de su Tabla 15, FNC / DT = 54.7%.
- La demanda de Ucayali, Loreto y Madre de Dios difiere entre estudios (censo regional vs. muestra expandida nacional); la oferta GTF y la ENA coinciden.
- En la ENA, la categoría "Otros Actos" de la base corresponde a PAS de inicio remitidos por las ARFFS (categoría no determinada).
