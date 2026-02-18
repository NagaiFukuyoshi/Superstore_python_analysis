# 🏢 Superstore Sales Dataset - Ejercicio Técnico para Data Analyst

## 📋 Descripción del Proyecto
Este repositorio contiene mi solución a un ejercicio técnico utilizando datos reales de ventas (Superstore dataset). El objetivo es demostrar mis habilidades en limpieza, transformación y análisis de datos con Python, así como mi capacidad para justificar decisiones técnicas y comunicar hallazgos de negocio.

## 🎯 Objetivo del Ejercicio
El objetivo de este ejercicio es demostrar la capacidad para:

- Entender datos sucios
- Tomar decisiones razonables
- Limpiar, transformar y analizar información con pandas
- Justificar tus elecciones
- Comunicar resultados de manera clara

## 🛠️ Tecnologías Utilizadas
- **Python 3** 
- **Pandas** - Limpieza y transformación de datos
- **NumPy** - Operaciones numéricas
- **Matplotlib / Seaborn** - Visualizaciones
- **Jupyter Notebooks** - Análisis interactivo
- **Git / GitHub** - Control de versiones

## 📁 Estructura del Proyecto

```
Superstore_python_analysis/
│
├── 📁 data/
│   ├── raw/
│   │   └── train.csv
│   └── processed/
│       └── train_limpio.csv
│
├── 📁 notebooks/
│   └── Superstore_python_analysis.ipynb
│
├── 📁 docs/
│   └── Superstore_python_justificacion.md
│
├── 📁 outputs/
│   └── 📁 graficos/
│       ├── Categorías_mas_vendidas.png
│       ├── Estados_donde_mas_compraron_Canon_imageCLASS_2200_Advanced_Copierventas_por_canal.png
│       ├── Frecuencia_de_compra_por_clientes_top_10.png
│       └── Promedio_de_compra_por_cliente_top_10.png
│       ├── Regiones_con_mas_ingresos_en_ventas.png
│       └── Top_5_clientes_que_mas_compraron.png
│       ├── Top_5_productos_que_mas_compraron_en_california.png
│       └── Top_10_estados_con_mayor_ingreso.png
│       ├── Top_10_meses_con_mayor_venta.png
│       └── Ventas_por_año.png
│       └── Ventas_por_productos.png
│
└── README.md
```


## 🔍 Problemas Encontrados y Soluciones Aplicadas

| Problema | Decisión | Justificación |
|----------|----------|---------------|
| Valores nulos en `postal_code` | No se modificó ni se rellenó los nulos | la cantidad era muy insignificante, además no se necesitaba para futuros análisis |
| Fechas en formato texto | Convertir a datetime con `dayfirst=True` | Habilitar análisis temporal con formato estándar |
| Nombres con diferentes formatos | Convertir los titulos de las columnas en minusculas y reemplazar " " y "-" por "_" | Evitar problemas con los nombres de las columnas en futuros análisis |
| Nombres largos en gráficos | Función con `textwrap` | Mejorar legibilidad de visualizaciones |

## 📊 Principales Hallazgos

### 1. Ventas por categoria 
Las 3 categorías están muy equilibradas:
- **Technology:**   827.456 USD
- **Furniture:**    728.659 USD
- **Office Supplies:**    705.422 USD

Diferencia de apenas 12 puntos porcentuales entre la primera y la tercera

### 2. Top 10 productos
- **Canon imageCLASS 2200 Advanced Copier:**                                          61599.824 USD - 2.72%
- **Fellowes PB500 Electric Punch Plastic Comb Binding Machine with Manual Bind:**    27453.384 USD - 1.21%
- **Cisco TelePresence System EX90 Videoconferencing Unit:**                          22638.480 USD - 1.00%
- **HON 5400 Series Task Chairs for Big and Tall:**                                   21870.576 USD - 0.97%
- **GBC DocuBind TL300 Electric Binding System:**                                     19823.479 USD - 0.88%
- **GBC Ibimaster 500 Manual ProClick Binding System:**                               19024.500 USD - 0.84%
- **Hewlett Packard LaserJet 3310 Copier:**                                           18839.686 USD - 0.83%
- **HP Designjet T520 Inkjet Large Format Printer - 24" Color:**                      18374.895 USD - 0.81%
- **GBC DocuBind P400 Electric Binding System:**                                      17965.068 USD - 0.79%
- **High Speed Automatic Electric Letter Opener:**                                    17030.312 USD - 0.75%
  
- Los productos **Canon imageCLASS 2200 Advanced Copier**, **Fellowes PB500 Electric Punch Plastic Comb Binding Machine with Manual Bind** y **Cisco TelePresence System EX90 Videoconferencing Unit** son los unicos que superan el 1% del total de los ingresos de los ultimos 4 años
  
### 3. Ventas por región
- **West:**       710219.6845 USD - 31.4%
- **East:**       669518.7260 USD - 29.6%
- **Central**     492646.9132 USD - 21.8%
- **South**       389151.4590 USD - 17.2%

- La región **West** casi duplica en ventas a la de menor rendimiento (**South**), adicionalmente las regiones de **West** y **East** aportaron mas del 60% del total de los ingresos en los ultimos 4 años (2015 - 2018)

### 4. Evolucion anual (2015 - 2018)
- **2016** tuvo una leve caída del -4.26% vs 2015
- **2017** se recupera fuertemente: +30.64%
- **2018** continúa el crecimiento: +20.30%
- Crecimiento acumulado 2015-2018: +50%

### 5. Mejor mes y año
- el **2018** fue sin dudas el mejor año, acumulando ingresos por 722.456 USD, asi mismo el mejor mes no solo del 2018, si no tambien de los ultimos 4 años (2015 - 2018) fue **Noviembre** con ingresos por 117,938 USD, ayudando en gran medida al gran crecimiento en ventas del años 2018.

### 6. Producto estrella
- **Canon imageCLASS 2200 Advanced Copier** es el producto más vendido del período **2015-2018**, con $61,599 USD en ingresos (2.72% del total).
- Solo 3 productos superan el 1% de participación individual: **el Canon**, **Fellowes PB50**0 y **Cisco TelePresence EX90**.

### 7. Clientes top
- Los 5 clientes que más aportan en ingresos son: **Sean Miller**, **Tamara Chand**, **Raymond Buch**, **Tom Ashbrook** y **Adrian Barton**.
- El producto preferido por este grupo es nuevamente el **Canon imageCLASS**.

### 8. Estados top
- **California** lidera con 19.73% de las ventas totales
- **New York** le sigue con 13.55%
- Ambos estados representan **1/3** de los ingresos totales de la empresa

## 📈 Visualizaciones

*Las visualizaciones generadas durante el análisis están disponibles en la carpeta outputs/graficos/ del repositorio.*

## 🚀 Cómo Reproducir el Análisis

### Requisitos previos
- Python 3.8 o superior
- pip (gestor de paquetes)

### Pasos
1. **Clonar el repositorio**
   ```bash
   git clone https://github.com/NagaiFukuyoshi/Superstore_python_analysis.git
   cd Superstore_python_analysis
   
### Instalar dependencias

- bash
  
pip install pandas numpy matplotlib seaborn jupyter
Ejecutar Jupyter Notebook

- bash
  
jupyter notebook
Abrir y ejecutar el archivo notebooks/Superstore_python_analysis.ipynb

### 💡 Decisiones Clave

- Todas las decisiones de limpieza y transformación están documentadas en detalle en docs/Superstore_python_justificacion.md. Las más importantes:

- Manejo de nulos en postal_code: Se decidió no modificar ni reemplazar los nulos.

- Estandarización de fechas: Formato datetime para análisis temporal robusto

- Datos faltantes en categorías: Imputación con moda para mantener consistencia

- Manejo de nombres con diferentes formatos: Converir los titulos de las columnas en minuscula y reemplazar los espacios (" ") y guiones medios ("-") por guiones bajos ("_") para evitar problemas con los nombres de las columnas en futuros analisis

- Manejo de nombres largos en gráficos: Se usó una función con `textwrap` para mejorar legibilidad de visualizaciones

### 📬 Contacto

- **Nombre:** Kevin Andres Arango

- **LinkedIn:** www.linkedin.com/in/kevin-vasquez-73547a29b

- **GitHub:** https://github.com/NagaiFukuyoshi

- **Correo:** vaskev1116@gmail.com

### 📝 Nota Final
Este proyecto fue desarrollado como parte de mi portafolio como aspirante a Data Analyst. Los datos fueron obtenidos de Kaggle y corresponden al dataset Superstore Sales.

⭐ Si te parece interesante, no olvides darle estrella al repositorio
