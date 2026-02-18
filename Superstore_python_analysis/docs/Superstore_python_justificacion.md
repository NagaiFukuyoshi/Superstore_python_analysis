# 🧠 Justificaciones Técnicas - # 🧠 Justificaciones Técnicas - Ejercicio Superstore Sales Dataset

## 📋 Resumen ejecutivo de decisiones

| Problema | Decisión | Justificación breve |
|----------|----------|---------------------|
| Valores nulos en `postal_code` | No se modificó ni se rellenó los nulos | la cantidad era muy insignificante, ademas no se necesitaba para futuros analisis |
| Fechas en formato texto | Convertir a datetime con `dayfirst=True` | Habilitar análisis temporal con formato estándar |
| Nombres con diferentes formatos | Converir los titulos de las columnas en minusculas y reemplazar " " y "-" por "_" | Evita problemas con los nombres de las columnas en futuros analisis |
| Nombres largos en gráficos | Función con `textwrap` | Mejorar legibilidad de visualizacione |

---

## 🔍 Detalle de cada decisión técnica

### 1. Valores nulos en `postal_code`

**Cantidad:** 11 registros (0.11% del total)

**Decisión:** No se cambió ni modificó los nulos de la columna, ya que el % no superaba el 5% ademas que de no se requeria para futuros analisis

**Código:**
```python

```

---

### 2. Fechas en formato texto

**Cantidad:** 9800 registros (100% del total)

**Decisión:** Convertir a datetime con `dayfirst=True` para luego procedes a extraer año, mes y dia para futuros analisis

**Código:**
```python
df['order_date'] = pd.to_datetime(df['order_date'], dayfirst=True, errors='coerce')
df['ship_date'] = pd.to_datetime(df['ship_date'], dayfirst=True, errors='coerce')
```

---

### 3. Nombres con diferentes formatos

**Cantidad:** 18 titulos de columnas (100% del total)

**Decisión:** Normalizar los titulos de las columnas, primero se convirtió todo en minuscula, y luego se reemplazo tanto los espacios " " y los guines medios "-" por guiones bajos "_"

**Código:**
```python
df.columns = (
    df.columns
    .str.lower()
    .str.replace(" ", "_")
    .str.replace("-", "_")
)

df.columns
```

---

### 4. Nombres largos en gráficos

**Cantidad:** nombres de los productos (100% del total)

**Decisión:** Crear función con textwrap para envolver texto

**Código:**
```python
def graficar_barras(datos, titulo, xlabel, ylabel, edgecolor='black', rotation=45, linestyle='--', alpha=0.7, width=20):
    
    # Envolver texto para que quepa
    nuevos_indices = []
    for idx in datos.index:
        # Dividir en líneas de máximo 'width' caracteres
        lineas = textwrap.wrap(str(idx), width=width)
        # Unir con saltos de línea
        nuevo_idx = '\n'.join(lineas)
        nuevos_indices.append(nuevo_idx)
    
    datos.index = nuevos_indices
    colores = plt.cm.Blues(np.linspace(0.4, 0.9, len(datos)))
    
    plt.figure(figsize=(12, 8))
    datos.plot(kind='bar', color=colores, edgecolor=edgecolor)
    plt.title(titulo, fontsize=14, fontweight='bold')
    plt.xlabel(xlabel)
    plt.ylabel(ylabel)
    plt.xticks(rotation=rotation, ha='center')
    plt.grid(axis='y', linestyle=linestyle, alpha=alpha)
    plt.tight_layout()
    plt.savefig(rf'C:\Users\ASUS\Desktop\Superstore_python_analysis\outputs\graficos\{titulo}_wrap.png', dpi=300, bbox_inches='tight')
    plt.show()
```