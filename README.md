# 🌍 ANÁLISIS GLOBAL: ESPERANZA DE VIDA Y BIENESTAR

---

## 📋 Índice Interactivo
1. [Descripción del Proyecto](#1-descripción-del-proyecto)
2. [Datasets Utilizados](#2-datasets-utilizados)
3. [Metodología y Análisis](#3-metodología-y-análisis)
4. [Resultados y Análisis Visual](#4-resultados-y-análisis-visual)
5. [Resultados Destacados](#5-resultados-destacados)

---

## 🏛️ 1. DESCRIPCIÓN DEL PROYECTO <a name="1-descripción-del-proyecto"></a>
Este proyecto de análisis cuantitativo evalúa cómo las variables macroeconómicas y los determinantes de salud pública impactan en la calidad de vida a nivel global. A través del procesamiento de bases de datos internacionales, el objetivo es comprender de qué manera el nivel de riqueza (PBI), de estudio y de salud pública (entre otras variables que analizaremos a continuación) se traduce en mejoras tangibles en las condiciones sanitarias y el bienestar social de la población.

---

## 🗄️ 2. DATASETS UTILIZADOS <a name="2-datasets-utilizados"></a>
El análisis se nutre de dos fuentes de datos principales (enfocadas en el año 2015):

### ⚕️ Life Expectancy Data
Registro histórico global de la Organización Mundial de la Salud (OMS) que incluye indicadores demográficos, tasas de mortalidad, nivel de escolaridad, inmunización (Hepatitis B, Polio, Difteria) y factores económicos (PBI). Las columnas de información dentro del dataset son las siguientes:
* **Country:** El nombre del país al que corresponden los indicadores registrados.
* **Year:** El año específico en el que se recolectaron los datos sociodemográficos y de salud.
* **Status:** La clasificación del nivel de desarrollo económico del país (Desarrollado o En vías de desarrollo).
* **Life expectancy:** La esperanza de vida promedio al nacer, expresada en años.
* **Adult Mortality:** La tasa de mortalidad de adultos, que mide la probabilidad de morir entre los 15 y 60 años (por cada 1.000 habitantes).
* **Infant deaths:** El número de muertes de niños menores de un año (por cada 1.000 nacidos vivos).
* **Alcohol:** El consumo anual per cápita de alcohol puro, medido en litros, en la población mayor de 15 años.
* **Percentage expenditure:** El gasto en salud expresado como porcentaje del Producto Bruto Interno (PBI) per cápita.
* **Hepatitis B:** El porcentaje de cobertura de inmunización contra la Hepatitis B en niños de un año de edad.
* **Measles:** El número total de casos reportados de sarampión por cada 1.000 habitantes.
* **BMI:** El Índice de Masa Corporal (IMC) promedio de toda la población del país.
* **Under-five deaths:** El número de muertes de niños menores de cinco años (por cada 1.000 nacidos vivos).
* **Polio:** El porcentaje de cobertura de inmunización contra la poliomielitis (Polio3) en niños de un año de edad.
* **Total expenditure:** El gasto gubernamental destinado a la salud, expresado como porcentaje del gasto total del Estado.
* **Diphtheria:** El porcentaje de cobertura de inmunización contra la difteria, tétanos y tos ferina (DTP3) en niños de un año.
* **HIV/AIDS:** La tasa de muertes causadas por el VIH/SIDA (por cada 1.000 nacidos vivos) en niños de 0 a 4 años.
* **GDP:** El Producto Bruto Interno (PBI) per cápita del país, expresado en dólares estadounidenses.
* **Population:** El volumen total de la población del país registrada en ese año.
* **Thinness 1-19 years:** El porcentaje de prevalencia de delgadez extrema y desnutrición en niños y adolescentes de 10 a 19 años.
* **Thinness 5-9 years:** El porcentaje de prevalencia de delgadez extrema y desnutrición en niños de 5 a 9 años.
* **Income composition of resources:** Un índice (escala de 0 a 1) relacionado con el Índice de Desarrollo Humano (IDH) que mide la eficiencia en la utilización de los recursos.
* **Schooling:** El número promedio de años de escolaridad formal que alcanza la población del país.

### 🌐 World Happiness Report (2015)
Reporte internacional que evalúa a los países según su puntaje de felicidad percibida, libertad y soporte social. Las columnas de información dentro del dataset son las siguientes:
* **Country:** El nombre del país evaluado en el reporte.
* **Year:** El año al que corresponden los datos de la encuesta.
* **Region:** La región geográfica o bloque continental al que pertenece el país.
* **Happiness Rank:** La posición numérica del país en el ranking mundial de felicidad (donde 1 representa al país más feliz).
* **Happiness Score:** El puntaje total de bienestar asignado al país, derivado de las encuestas ciudadanas (escala de 0 a 10).
* **Standard Error:** El margen de error estadístico estimado para el puntaje de felicidad obtenido.
* **Economy (GDP per Capita):** La magnitud en la que el Producto Bruto Interno per cápita contribuye matemáticamente al puntaje total de felicidad.
* **Family:** La medida en la que el apoyo social percibido (contar con familiares o amigos en tiempos de necesidad) influye en el bienestar.
* **Health (Life Expectancy):** La contribución estadística de la esperanza de vida saludable de la población al puntaje final de felicidad.
* **Freedom:** El impacto que tiene la percepción ciudadana sobre su libertad para tomar decisiones vitales importantes.
* **Trust (Government Corruption):** La medida en la que la percepción de bajos niveles de corrupción gubernamental y empresarial aporta a la felicidad.
* **Generosity:** La medida en la que los actos solidarios de los ciudadanos (como donaciones a la caridad) contribuyen al puntaje total.
* **Dystopia Residual:** Un valor de ajuste estadístico que compara al país con "Distopía" (un país hipotético con los peores resultados posibles) y engloba los factores que no se explican por las otras seis variables.

---

## ⚙️ 3. METODOLOGÍA Y ANÁLISIS <a name="3-metodología-y-análisis"></a>
A lo largo de este proyecto, aplicamos diversas herramientas de análisis de datos en Python (utilizando la librería Pandas y Scikit-Learn), evolucionando desde la exploración descriptiva hasta el modelado predictivo. A continuación, detallamos el propósito teórico de cada función y su aplicación específica en nuestro análisis:

### 🔬 1. Exploración y Limpieza de Datos `[head(), info(), dropna(), sort_values()]`
* **¿Para qué sirve?** Es el primer paso de cualquier análisis. Estas funciones permiten diagnosticar la estructura del dataset (cantidad de filas y columnas), identificar el tipo de dato de cada variable (texto, números enteros o decimales), detectar valores faltantes (nulos) que podrían arruinar los cálculos, y ordenar los datos para encontrar los casos extremos (máximos y mínimos).
* **Nuestra aplicación en el proyecto:** Utilizamos `head()` e `info()` para entender la estructura original de los datos de la OMS y del Happiness Report. Aplicamos `dropna()` para eliminar registros incompletos que afectaban las métricas de salud. Finalmente, usamos `sort_values()` para crear los rankings de los países con mayor y menor expectativa de vida, filtrando los "Top 30" y "Bottom 30" para nuestros gráficos interactivos.

### 🗂️ 2. Agrupamiento Estratégico `[groupby()]`
* **¿Para qué sirve?** Pasa del análisis de filas individuales al análisis de segmentos de negocio. Agrupa los datos según una variable categórica (como países, regiones o años) y permite calcular métricas agregadas (sumas totales, promedios, conteos) para comparar el rendimiento entre distintos grupos.
* **Nuestra aplicación en el proyecto:** Lo implementamos para agrupar los datos globales por continentes (`Region`). Gracias a esto, pudimos calcular el promedio de PBI y de Esperanza de Vida a nivel regional, lo que nos permitió visualizar macroeconómicamente las disparidades entre distintos bloques geográficos, en lugar de analizar casi 200 países de forma aislada.

### 🔗 3. Integración de Datasets `[merge()]`
* **¿Para qué sirve?** Es la herramienta clave para unificar múltiples fuentes de información. Funciona cruzando dos bases de datos distintas a través de una columna que tengan en común (la "llave"), enriqueciendo el análisis al permitir cruzar variables que originalmente estaban separadas.
* **Nuestra aplicación en el proyecto:** Fue fundamental para nuestro análisis central. Utilizamos `merge()` para unir el dataset de la OMS (que contenía métricas duras de salud y economía) con el World Happiness Report de 2015 (que contenía métricas de percepción social). Usamos la columna del nombre del país (`Country`) como llave de unión, logrando un único dataframe que nos permitió cruzar, por ejemplo, el PBI per cápita con el puntaje de felicidad.

### ⚖️ 4. Diseño de KPIs e Índices Propios (Scoring)
* **¿Para qué sirve?** Un KPI (Key Performance Indicator) resume el rendimiento en un solo número. El modelado de Scoring va un paso más allá: permite evaluar y rankear elementos asignándoles distintos pesos (ponderación matemática) a múltiples variables, creando un índice propio que refleja el éxito o el riesgo según los criterios del analista.
* **Nuestra aplicación en el proyecto:** En lugar de mirar variables sueltas, diseñamos dos modelos matemáticos propios:
  1. **Score de Riesgo Sanitario:** Aislamos factores epidemiológicos (como tasas de Polio, Difteria y Hepatitis) para rankear qué países tenían los sistemas de inmunización más vulnerables.
  2. **Score de Bienestar Integral:** Creamos un índice ponderado muy robusto que premia el impacto positivo de la Esperanza de vida (40% de peso), el PBI (30%) y la Educación (10%), mientras penaliza fuertemente las tasas de mortalidad y prevalencia del VIH (20%).

### 🔮 5. Modelado Predictivo (Regresión Lineal y Forecast)
* **¿Para qué sirve?** Representa el salto del análisis descriptivo (qué pasó) al análisis predictivo (qué pasará). Utiliza algoritmos de Machine Learning para aprender el comportamiento histórico de los datos, trazar una tendencia matemática y estimar valores futuros, cuantificando la incertidumbre mediante métricas de precisión.
* **Nuestra aplicación en el proyecto:** Importamos la librería `Scikit-Learn` y entrenamos un modelo de `LinearRegression` utilizando el historial económico de los países. A partir de esta tendencia, hicimos un Forecast para proyectar el crecimiento del PBI mundial hacia el año 2025. Además, calculamos métricas de validación como el R2 (R-cuadrado) y el Error Absoluto Medio (MAE) para demostrar la confiabilidad estadística de nuestra proyección macroeconómica.

### 📊 6. Visualización Estratégica de Datos (Matplotlib, Seaborn y Plotly)
* **¿Para qué sirve?** La visualización de datos es una herramienta analítica fundamental. Sirve para traducir relaciones numéricas complejas en formatos visuales intuitivos. Esto permite a los analistas y tomadores de decisiones identificar rápidamente tendencias, valores atípicos (outliers) y la fuerza de las correlaciones entre distintas variables (como salud y economía) que serían imposibles de detectar leyendo únicamente tablas de datos crudos.
* **Nuestra aplicación en el proyecto:** Implementamos cuatro niveles de visualización para dar soporte a nuestras conclusiones:
  1. **Análisis Bivariado (Matplotlib y Seaborn):** Generamos gráficos de dispersión estáticos para comprobar visualmente la teoría económica (ej. cómo reacciona la esperanza de vida a medida que aumenta la escolaridad o el PBI).
  2. **Evolución Temporal con Doble Eje Y (twinx):** Diseñamos gráficos de líneas superpuestos para analizar la evolución histórica de variables con magnitudes completamente distintas (por ejemplo, contrastar años de vida vs. inversión en salud pública) sin distorsionar la escala visual.
  3. **Visualización Interactiva (Plotly Express):** Creamos gráficos de burbujas dinámicos cruzando el Happiness Score con la Esperanza de Vida, donde el tamaño de cada burbuja representa el peso económico (PBI) del país. Además, personalizamos el Hover (la etiqueta al pasar el mouse) inyectando HTML para mostrar las banderas nacionales de manera profesional.
  4. **Visualización de Tendencias y Forecast (Gráfico Predictivo):** Contrastamos visualmente la línea de datos históricos reales del PBI con la proyección futura hacia el año 2025 estimada por nuestro modelo de regresión. Esto permite traducir el pronóstico matemático de Machine Learning en un formato intuitivo, facilitando el análisis de la expectativa de crecimiento económico global.
  5. **Rankings y Segmentación de Extremos `[sort_values(), head()]`:** Utilizamos `sort_values()` combinado con `head()` para generar rankings precisos. Aislamos el "Top 10" y el "Top 30" de países con mayor Esperanza de Vida y mejor puntaje en el Happiness Score. Esto nos permitió limpiar el ruido visual en los gráficos (evitando saturar la pantalla con casi 200 países) y enfocar nuestras conclusiones estratégicas en los líderes mundiales.

---

## 📊 4. RESULTADOS Y ANÁLISIS VISUAL <a name="4-resultados-y-análisis-visual"></a>

En esta sección incluimos y analizamos en profundidad las visualizaciones clave que dan soporte empírico a toda nuestra investigación[cite: 1]. Los hallazgos se estructuran desde la evaluación de la frontera biológica global, pasando por auditorías de eficiencia estatal, hasta el modelado predictivo del futuro demográfico[cite: 1].

### 🌐 1. Extremos Globales de Longevidad: La Brecha Demográfica
El análisis de los extremos del espectro global nos permite entender los límites biológicos y las urgencias humanitarias actuales.

* **Título:** Top 10 Países con Mayor Expectativa de Vida (La Frontera Alta).
* **Lectura Técnica:** Gráfico de barras horizontales aislando a los líderes mundiales (año 2015).
* **Insight Analítico:** Países como Eslovenia y Dinamarca lideran el ranking muy pegados por encima de los 80 años[cite: 1]. Se observa una bajísima dispersión entre los primeros puestos, lo que sugiere la existencia de un "techo biológico y social" donde las sociedades avanzadas tienden a converger en un límite provisorio de supervivencia, dado el estado actual de la medicina[cite: 1].

> 📌 **[INSERTAR GRÁFICO AQUÍ: Top 10 Mayor Expectativa]**
> `[![Top 10 Mayor Expectativa](URL_DE_TU_IMAGEN_PNG_AQUI)](URL_GITHACK_SI_ES_INTERACTIVO_O_BORRAR_PARENTESIS)`

* **Título:** Top 10 Países con Menor Expectativa de Vida (La Base de la Pirámide).
* **Lectura Técnica:** Gráfico de barras horizontales enfocado en el percentil inferior global.
* **Insight Analítico:** Naciones como Sierra Leona y Chad registran expectativas de vida que apenas rozan los 50 años[cite: 1]. Este gráfico visualiza una brecha global de longevidad de más de 30 años entre los extremos, siendo un reflejo directo de crisis epidemiológicas crónicas (como el impacto del HIV) y la falta severa de infraestructura básica[cite: 1].

> 📌 **[INSERTAR GRÁFICO AQUÍ: Top 10 Menor Expectativa]**
> `[![Top 10 Menor Expectativa](URL_DE_TU_IMAGEN_PNG_AQUI)](URL_GITHACK_SI_ES_INTERACTIVO_O_BORRAR_PARENTESIS)`

### 📉 2. Caso de Estudio Nacional: Volatilidad Macroeconómica vs. Demografía
Evaluamos el comportamiento de Argentina como un laboratorio perfecto para cruzar shocks financieros con indicadores de salud a lo largo del tiempo.

* **Título:** Evolución de la Expectativa de Vida vs. PBI en Argentina.
* **Lectura Técnica:** Gráfico de evolución histórica temporal con doble eje Y (`twinx`), contrastando PBI en dólares y Años de Vida.
* **Insight Analítico:** Mientras la línea del PBI argentino muestra caídas brutales y ciclos de crisis profundos, la línea de la esperanza de vida mantiene un crecimiento inercial, lento pero constante, casi inmune a los shocks financieros de corto plazo[cite: 1]. Esto valida nuestra *Hipótesis 1*: la longevidad no depende de la billetera del momento, sino de factores estructurales de largo plazo[cite: 1].

> 📌 **[INSERTAR GRÁFICO AQUÍ: Expectativa vs PBI Arg]**
> `[![Evolución PBI vs Expectativa](URL_DE_TU_IMAGEN_PNG_AQUI)](URL_GITHACK_SI_ES_INTERACTIVO_O_BORRAR_PARENTESIS)`

### 🏛️ 3. Auditoría de Eficiencia Institucional
Profundizamos en el desempeño del Estado argentino para medir el impacto real de sus políticas públicas en la salud de la población.

* **Título:** Evolución de la Expectativa de Vida vs. Inversión en Salud Pública en Argentina.
* **Lectura Técnica:** Gráfico de doble eje Y que cruza longevidad contra el porcentaje del presupuesto destinado a la salud[cite: 1].
* **Insight Analítico:** Al analizar las curvas, descubrimos que los incrementos presupuestarios no se traducen de forma inmediata o lineal en más años de vida[cite: 1]. Existe un rezago temporal evidente y períodos de clara ineficiencia marginal[cite: 1]. Esto demuestra empíricamente que gastar más no sirve si se gasta de forma burocrática o centralizada[cite: 1].

> 📌 **[INSERTAR GRÁFICO AQUÍ: Expectativa vs Inversión Salud]**
> `[![Inversión en Salud](URL_DE_TU_IMAGEN_PNG_AQUI)](URL_GITHACK_SI_ES_INTERACTIVO_O_BORRAR_PARENTESIS)`

### 🧠 4. El Capital Humano como Escudo Estructural
Contrastamos la variable educativa para evaluar su peso relativo frente a las métricas económicas tradicionales.

* **Título:** Evolución de la Expectativa de Vida vs. Nivel de Escolaridad en Argentina.
* **Lectura Técnica:** Gráfico de evolución temporal superponiendo Esperanza de Vida y Años promedio de escolaridad[cite: 1].
* **Insight Analítico:** A diferencia del PBI o del gasto sanitario, la curva de años promedio de estudio se desplaza con un paralelismo estructural asombroso junto a la línea de esperanza de vida; la sincronía es casi perfecta[cite: 1]. Esto aporta un respaldo empírico rotundo a nuestra *Hipótesis 2*: la educación y el capital humano son los verdaderos cimientos que sostienen el progreso demográfico y blindan a la población ante las crisis[cite: 1].

> 📌 **[INSERTAR GRÁFICO AQUÍ: Expectativa vs Escolaridad]**
> `[![Escolaridad vs Expectativa](URL_DE_TU_IMAGEN_PNG_AQUI)](URL_GITHACK_SI_ES_INTERACTIVO_O_BORRAR_PARENTESIS)`

### ⚕️ 5. Radiografía Global del Bienestar (Merge de Datos)
El cruce definitivo entre las métricas biométricas de la OMS y los datos perceptivos de las encuestas ciudadanas globales.

* **Título:** Expectativa de Vida vs. Puntuación de Felicidad.
* **Lectura Técnica:** Gráfico de dispersión/burbujas dinámico. Cruza salud biológica con felicidad autopercibida, agrupando por clusters regionales (continentes)[cite: 1].
* **Insight Analítico:** Los puntos dibujan una clarísima tendencia ascendente. Las regiones del mundo se agrupan en clusters: las sociedades con redes de apoyo sólidas, libertad personal y baja corrupción (ubicadas en el cuadrante superior derecho) viven sustancialmente más tiempo[cite: 1]. Esto demuestra que la salud del cuerpo está fuertemente ligada al bienestar social y emocional del entorno[cite: 1].

> 📌 **[INSERTAR GRÁFICO AQUÍ: Expectativa vs Felicidad]**
> `[![Expectativa vs Felicidad](URL_DE_TU_IMAGEN_PNG_AQUI)](URL_GITHACK_SI_ES_INTERACTIVO_O_BORRAR_PARENTESIS)`

### ⚖️ 6. Evaluación Multidimensional: El Ranking de Scoring
Aplicación de nuestro KPI de diseño propio para evaluar a las naciones superando el sesgo tradicional de la medición exclusiva por PBI.

* **Título:** Top Países Líderes y Rezagados según Score de Bienestar y Salud (2015).
* **Lectura Técnica:** Gráfico de barras horizontales divergentes aplicando nuestro modelo matemático ponderado (40% Vida, 30% Educación, 20% Felicidad, 10% PBI)[cite: 1].
* **Insight Analítico:** La gran conclusión estratégica de este modelo es que los países pintados en verde que dominan la cima del Score no son necesariamente las superpotencias financieras más ricas del planeta[cite: 1]. Son aquellos países que logran el equilibrio óptimo entre desarrollo económico, capital humano robusto y altos niveles de felicidad[cite: 1]. Es la validación empírica absoluta de nuestra Hipótesis de Eficiencia[cite: 1].

> 📌 **[INSERTAR GRÁFICO AQUÍ: Barras de Scoring]**
> `[![Scoring Multidimensional](URL_DE_TU_IMAGEN_PNG_AQUI)](URL_GITHACK_SI_ES_INTERACTIVO_O_BORRAR_PARENTESIS)`

### 🔭 7. Proyección Estratégica (Machine Learning Forecast)
Transición del análisis descriptivo a la consultoría predictiva utilizando algoritmos de regresión.

* **Título:** Pronóstico Interactivo de la Expectativa de Vida.
* **Lectura Técnica:** Gráfico de series de tiempo proyectado hacia la próxima década mediante algoritmos predictivos, incluyendo sombreado de intervalos de confianza[cite: 1].
* **Insight Analítico:** El modelo calcula que, si las condiciones e inversiones estructurales mantienen su inercia histórica, la esperanza de vida global continuará con una tendencia de crecimiento moderado y sostenido[cite: 1]. Esta proyección ofrece una base estadística sólida para la planificación estratégica y el desarrollo de políticas públicas a largo plazo[cite: 1].

> 📌 **[INSERTAR GRÁFICO AQUÍ: Forecast Expectativa / GDP]**
> `[![Forecast Machine Learning](URL_DE_TU_IMAGEN_PNG_AQUI)](URL_GITHACK_SI_ES_INTERACTIVO_O_BORRAR_PARENTESIS)`

* **Título:** Proyección Macroeconómica: Evolución del PBI Global hacia 2025.
* **Lectura Técnica:** Gráfico de tendencias que superpone los datos históricos reales del PBI con la recta predictiva generada por nuestro modelo de Regresión Lineal proyectada hacia la próxima década.
* **Insight Macroeconómico:** El modelo estadístico confirma una tendencia de base alcista para la economía global, sustentada por un alto nivel de precisión métrica (R2). Sin embargo, desde una óptica de planificación estratégica, este escenario "Base" asume una continuidad histórica y deberá ser ajustado ante potenciales shocks externos (como crisis financieras o coyunturas pandémicas) que puedan alterar la pendiente de crecimiento proyectada por el algoritmo.

> 📌 **[INSTRUCCIÓN PARA INSERTAR GRÁFICO AQUÍ]**
> `[![Forecast PBI](URL_IMAGEN_PNG_AQUI)](URL_GITHACK_INTERACTIVO_AQUI)`
---

## 📌 5. RESULTADOS DESTACADOS <a name="5-resultados-destacados"></a>

IDEA TEMPORAL (Le dije a la IA que hiciera una. Luego hago una conclusión)

A través de la integración y modelado de datos sociodemográficos y económicos globales, este proyecto demuestra empíricamente que la riqueza nacional (PBI) es una condición necesaria, pero no suficiente, para garantizar el bienestar integral de la población.

Los hallazgos clave de nuestro análisis revelan que:
* **El desarrollo tiene rendimientos decrecientes:** El impacto del crecimiento económico en la esperanza de vida es masivo en etapas iniciales de desarrollo (logrando sacar a poblaciones de la pobreza extrema), pero se estabiliza en economías avanzadas si no se acompaña de políticas de salud eficientes.
* **El Capital Humano es el verdadero motor:** La inversión sostenida en educación (Escolaridad) demostró tener una correlación directa y estructural con la longevidad, actuando como un escudo protector frente a la volatilidad macroeconómica (como se observó en el caso de Argentina).
* **La eficiencia estatal salva vidas:** Nuestros modelos de Scoring confirmaron que los países líderes no son exclusivamente los de mayor PBI bruto, sino aquellos que logran traducir su presupuesto en un control epidemiológico efectivo y en la reducción de la mortalidad prematura.

Finalmente, aunque nuestro modelo predictivo (Forecast) proyecta un escenario base de crecimiento económico global continuo hacia 2025, el desafío real para los tomadores de decisiones será utilizar el análisis de datos para asegurar que dicha expansión financiera se convierta en eficiencia sanitaria, resiliencia demográfica y felicidad real.
