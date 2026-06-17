# 🌍 ANÁLISIS GLOBAL: ESPERANZA DE VIDA, DESARROLLO ECONÓMICO Y BIENESTAR

## 📋 DESCRIPCIÓN DEL PROYECTO
Este proyecto de análisis cuantitativo evalúa cómo las variables macroeconómicas y los determinantes de salud pública impactan en la calidad de vida a nivel global. A través del procesamiento de bases de datos internacionales, el objetivo es comprender de qué manera el nivel de riqueza (PBI), de estudio y de salud pública se traduce en mejoras tangibles en las condiciones sanitarias y el bienestar social de la población.

---

## 🗂️ DATASETS UTILIZADOS
El análisis se nutre de dos fuentes de datos principales enfocadas en el año 2015:

### 🏥 Life Expectancy Data (OMS)
Registro histórico global de la Organización Mundial de la Salud (OMS) que incluye indicadores demográficos, tasas de mortalidad, nivel de escolaridad, inmunización y factores económicos:
* **Country & Year:** País y año específico de los datos.
* **Status:** Clasificación del nivel de desarrollo económico.
* **Life expectancy:** Esperanza de vida promedio al nacer (años).
* **Adult & Infant Mortality:** Tasas de mortalidad adulta e infantil.
* **Percentage & Total expenditure:** Gasto en salud expresado como % del PBI per cápita y como % del gasto total del Estado.
* **Inmunización y Enfermedades:** Cobertura de Hepatitis B, Polio, Diphtheria, y prevalencia de Measles y HIV/AIDS.
* **Factores socioeconómicos:** GDP (PBI per cápita), Population (Población) y Schooling (Años promedio de escolaridad formal).

### 🌟 World Happiness Report (2015)
Reporte internacional que evalúa a los países según su puntaje de felicidad percibida, libertad y soporte social:
* **Happiness Rank & Score:** Posición global y puntaje total de bienestar percibido (escala 0-10).
* **Economy (GDP per Capita):** Contribución del PBI al puntaje de felicidad.
* **Family & Freedom:** Impacto del apoyo social y la libertad de decisión.
* **Health (Life Expectancy):** Contribución de la esperanza de vida saludable.
* **Trust (Government Corruption) & Generosity:** Percepción de corrupción y niveles de solidaridad.

---

## 🛠️ METODOLOGÍA Y ANÁLISIS
A lo largo de este proyecto, aplicamos diversas herramientas de análisis de datos en Python (Pandas y Scikit-Learn), evolucionando desde la exploración descriptiva hasta el modelado predictivo:

1. **Exploración y Limpieza de Datos (`head`, `info`, `dropna`, `sort_values`):** Diagnóstico de estructura, detección de valores nulos que afectaban las métricas de salud, y creación de rankings ("Top 30" y "Bottom 30").
2. **Agrupamiento Estratégico (`groupby`):** Segmentación por continentes para visualizar macroeconómicamente las disparidades entre bloques geográficos.
3. **Integración de Datasets (`merge`):** Unión de la base de la OMS (métricas duras) con el Happiness Report (percepción social) usando la columna `Country` como llave, logrando un único dataframe consolidado.
4. **Diseño de KPIs e Índices Propios (Scoring):**
   * **Score de Riesgo Sanitario:** Aislamiento de factores epidemiológicos para rankear vulnerabilidad inmunológica.
   * **Score de Bienestar Integral:** Índice ponderado que premia Esperanza de Vida (40%), PBI (10%) y Educación (30%), penalizando fuertemente la mortalidad.
5. **Modelado Predictivo (Regresión Lineal y Forecast):** Entrenamiento de un algoritmo de Machine Learning para aprender el comportamiento histórico y estimar valores futuros, cuantificando la precisión mediante el R2 y MAE.
6. **Visualización Estratégica (Matplotlib, Seaborn, Plotly):** Creación de gráficos interactivos de burbujas, evolución temporal con doble eje Y, y visualización de tendencias para contrastar el Forecast.

---

## 📈 RESULTADOS Y ANÁLISIS VISUAL

### 1. El Panorama Global (Gráfico de Burbujas)
* **Radiografía Global: Felicidad, Longevidad y Poder Económico:** Las economías de Europa Occidental y Norteamérica demuestran que un alto volumen económico cataliza el desarrollo social. En contraste, las naciones del África Subsahariana evidencian una trampa de pobreza donde el bajo PBI limita la infraestructura sanitaria.
> *(Reemplazá los links de abajo por tu imagen estática subida a GitHub y tu link de githack)*
> [![Radiografía Global](https://url_de_tu_imagen_aqui.png)](https://url_de_tu_grafico_interactivo_aqui.html)

### 2. Relaciones Causales
* **El Impacto del Crecimiento Económico en la Longevidad:** Se demuestra una curva de "rendimientos decrecientes". El PBI tiene un límite biológico; en economías avanzadas, más riqueza no se traduce linealmente en más vida.
* **El Capital Humano como Motor:** Fuerte correlación positiva. Una población educada no solo es más longeva, sino más productiva para la matriz empresarial.
* **El Costo de la Mortalidad Prematura:** Reducir la mortalidad infantil es la inversión con el ROI social más alto.
* **Impacto Epidemiológico:** Shocks como el VIH destruyen la Población Económicamente Activa (PEA), generando círculos viciosos de presión fiscal.

### 3. Zonas Críticas y Eficiencia Estatal (Caso Argentina)
* **Resiliencia Sanitaria:** La asimetría entre economía y demografía muestra que las crisis del PBI argentino no desploman la esperanza de vida automáticamente.
* **Análisis de Eficiencia del Gasto Público:** Al analizar las curvas en el tiempo, descubrimos que los incrementos presupuestarios no se traducen de forma inmediata o lineal en más años de vida[cite: 80]. Existe un rezago temporal evidente y períodos de clara ineficiencia marginal[cite: 81]. Esto demuestra empíricamente la utilidad de nuestro KPI de eficiencia: gastar más no sirve si se gasta de forma burocrática o centralizada.
* **Efecto Compuesto de la Inversión Institucional:** El crecimiento paralelo de la escolaridad y la esperanza de vida confirma el blindaje social del capital humano a largo plazo.

### 4. Proyección Estratégica (Forecast)
* **Evolución del PBI Global hacia 2025:** El modelo confirma una tendencia base alcista, aunque debe ser ajustada ante potenciales shocks externos o crisis geopolíticas no contempladas en el modelo histórico.

---

## 🎯 RESULTADOS DESTACADOS (CONCLUSIONES)
Este proyecto demuestra empíricamente que la riqueza nacional (PBI) es una condición necesaria, pero **no suficiente**, para garantizar el bienestar integral:

* **El desarrollo tiene rendimientos decrecientes:** El impacto económico es masivo para salir de la pobreza extrema, pero se estabiliza en economías avanzadas.
* **El Capital Humano es el verdadero motor:** La educación (Escolaridad) actúa como un escudo protector estructural frente a la volatilidad macroeconómica.
* **La eficiencia estatal salva vidas:** Los líderes mundiales en los modelos de Scoring no son solo los de mayor PBI, sino los que traducen su presupuesto en control epidemiológico efectivo.

El desafío real para los tomadores de decisiones empresariales y gubernamentales será utilizar estos datos para asegurar que la expansión financiera se convierta en eficiencia sanitaria, resiliencia demográfica y felicidad real.
