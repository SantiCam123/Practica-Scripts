# Practica-Scripts

# 🧾 Sales Clean & Report CLI

Este proyecto implementa una **aplicación de línea de comandos (CLI)** en Python que permite **filtrar pedidos, calcular KPIs y generar reportes** a partir de un archivo CSV.  
El objetivo fue construir una herramienta automatizada capaz de limpiar, resumir y exportar información de ventas aplicando filtros opcionales por fecha y país.

---

## ⚙️ Descripción del Proyecto

La aplicación recibe como entrada un archivo CSV con pedidos (por ejemplo, `orders_sample.csv`) y, mediante diferentes argumentos en consola, permite:

- Aplicar filtros por **rango de fechas** (`--start`, `--end`) y por **país** (`--country`).
- Calcular los KPIs más importantes sobre los pedidos con `status="paid"`:
  - **num_orders** → número total de pedidos.
  - **total_revenue** → ingresos totales (unidades × precio unitario).
  - **avg_order_value** → valor medio del pedido.
- Exportar los resultados en formato **TXT** o **JSON**.
- Guardar, de forma opcional, un CSV con los datos filtrados.

El script fue desarrollado como una práctica integral de:
- Manejo de **argumentos con `argparse`**.
- Lectura y filtrado de datos con **Pandas**.
- Escritura de resultados en archivos de salida.
- Uso de **códigos de salida coherentes** (`0`, `1`, `2`).
- Validaciones, logs e integración modular con el entorno del proyecto.

---

## 🧩 Argumentos implementados

| Argumento | Tipo | Descripción |
|------------|------|--------------|
| `--input` | Obligatorio | Ruta al CSV de pedidos. |
| `--outdir` | Opcional | Directorio de salida (por defecto: `outputs`). |
| `--start` | Opcional | Fecha de inicio (formato `YYYY-MM-DD`). |
| `--end` | Opcional | Fecha de fin (formato `YYYY-MM-DD`). |
| `--country` | Opcional | Código del país (por ejemplo: `ES`, `FR`, `UK`). |
| `--summary-format` | Opcional | Formato del resumen: `txt` o `json` (por defecto: `txt`). |
| `--export-filtered` | Flag | Guarda un CSV con los pedidos filtrados. |

Ejemplo de uso:

```bash
python3 src/sales_cli.py --input data/raw/orders_sample.csv \
  --start 2025-10-01 --end 2025-10-03 --country ES \
  --summary-format json --export-filtered