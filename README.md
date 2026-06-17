## Gryffindorr
##ANÁLISIS GLOBAL: ESPERANZA DE VIDA, DESARROLLO ECONÓMICO Y BIENESTAR
#DESCRIPCIÓN DEL PROYECTO:
Este proyecto de análisis cuantitativo evalúa cómo las variables macroeconómicas y los determinantes de salud pública impactan en la calidad de vida a nivel global. A través del procesamiento de bases de datos internacionales, el objetivo es comprender de qué manera el nivel de riqueza (PBI), de estudio y de salud pública (entre otras variables que analizaremos a continuación) se traduce en mejoras tangibles en las condiciones sanitarias y el bienestar social de la población.

#DATASETS UTILIZADOS:
El análisis se nutre de dos fuentes de datos principales (enfocadas en el año 2015):

	Life Expectancy Data: Registro histórico global de la Organización Mundial de la Salud (OMS) que incluye indicadores demográficos, tasas de mortalidad, nivel de escolaridad, inmunización (Hepatitis B, Polio, Difteria) y factores económicos (PBI). Las columnas de información dentro del dataset son las siguientes:
 
o	Country: El nombre del país al que corresponden los indicadores registrados.
o	Year: El año específico en el que se recolectaron los datos sociodemográficos y de salud.
o	Status: La clasificación del nivel de desarrollo económico del país (Desarrollado o En vías de desarrollo).
o	Life expectancy: La esperanza de vida promedio al nacer, expresada en años.
o	Adult Mortality: La tasa de mortalidad de adultos, que mide la probabilidad de morir entre los 15 y 60 años (por cada 1.000 habitantes).
o	Infant deaths: El número de muertes de niños menores de un año (por cada 1.000 nacidos vivos).
o	Alcohol: El consumo anual per cápita de alcohol puro, medido en litros, en la población mayor de 15 años.
o	Percentage expenditure: El gasto en salud expresado como porcentaje del Producto Bruto Interno (PBI) per cápita.
o	Hepatitis B: El porcentaje de cobertura de inmunización contra la Hepatitis B en niños de un año de edad.
o	Measles: El número total de casos reportados de sarampión por cada 1.000 habitantes.
o	BMI: El Índice de Masa Corporal (IMC) promedio de toda la población del país.
o	Under-five deaths: El número de muertes de niños menores de cinco años (por cada 1.000 nacidos vivos).
o	Polio: El porcentaje de cobertura de inmunización contra la poliomielitis (Polio3) en niños de un año de edad.
o	Total expenditure: El gasto gubernamental destinado a la salud, expresado como porcentaje del gasto total del Estado.
o	Diphtheria: El porcentaje de cobertura de inmunización contra la difteria, tétanos y tos ferina (DTP3) en niños de un año.
o	HIV/AIDS: La tasa de muertes causadas por el VIH/SIDA (por cada 1.000 nacidos vivos) en niños de 0 a 4 años.
o	GDP: El Producto Bruto Interno (PBI) per cápita del país, expresado en dólares estadounidenses.
o	Population: El volumen total de la población del país registrada en ese año.
o	Thinness 1-19 years: El porcentaje de prevalencia de delgadez extrema y desnutrición en niños y adolescentes de 10 a 19 años.
o	Thinness 5-9 years: El porcentaje de prevalencia de delgadez extrema y desnutrición en niños de 5 a 9 años.
o	Income composition of resources: Un índice (escala de 0 a 1) relacionado con el Índice de Desarrollo Humano (IDH) que mide la eficiencia en la utilización de los recursos.
o	Schooling: El número promedio de años de escolaridad formal que alcanza la población del país.

 
	World Happiness Report (2015): Reporte internacional que evalúa a los países según su puntaje de felicidad percibida, libertad y soporte social. Las columnas de información dentro del dataset son las siguientes:
o	Country: El nombre del país evaluado en el reporte.
o	Year: El año al que corresponden los datos de la encuesta.
o	Region: La región geográfica o bloque continental al que pertenece el país.
o	Happiness Rank: La posición numérica del país en el ranking mundial de felicidad (donde 1 representa al país más feliz).
o	Happiness Score: El puntaje total de bienestar asignado al país, derivado de las encuestas ciudadanas (escala de 0 a 10).
o	Standard Error: El margen de error estadístico estimado para el puntaje de felicidad obtenido.
o	Economy (GDP per Capita): La magnitud en la que el Producto Bruto Interno per cápita contribuye matemáticamente al puntaje total de felicidad.
o	Family: La medida en la que el apoyo social percibido (contar con familiares o amigos en tiempos de necesidad) influye en el bienestar.
o	Health (Life Expectancy): La contribución estadística de la esperanza de vida saludable de la población al puntaje final de felicidad.
o	Freedom: El impacto que tiene la percepción ciudadana sobre su libertad para tomar decisiones vitales importantes.
o	Trust (Government Corruption): La medida en la que la percepción de bajos niveles de corrupción gubernamental y empresarial aporta a la felicidad.
o	Generosity: La medida en la que los actos solidarios de los ciudadanos (como donaciones a la caridad) contribuyen al puntaje total.
o	Dystopia Residual: Un valor de ajuste estadístico que compara al país con "Distopía" (un país hipotético con los peores resultados posibles) y engloba los factores que no se explican por las otras seis variables. 
 
#METODOLOGÍA Y ANÁLISIS:
A lo largo de este proyecto, aplicamos diversas herramientas de análisis de datos en Python (utilizando la librería Pandas y Scikit-Learn), evolucionando desde la exploración descriptiva hasta el modelado predictivo. A continuación, detallamos el propósito teórico de cada función y su aplicación específica en nuestro análisis:

1. Exploración y Limpieza de Datos [head(), info(), dropna(), sort_values()]:
•	¿Para qué sirve? Es el primer paso de cualquier análisis. Estas funciones permiten diagnosticar la estructura del dataset (cantidad de filas y columnas), identificar el tipo de dato de cada variable (texto, números enteros o decimales), detectar valores faltantes (nulos) que podrían arruinar los cálculos, y ordenar los datos para encontrar los casos extremos (máximos y mínimos).
•	Nuestra aplicación en el proyecto: Utilizamos head() e info() para entender la estructura original de los datos de la OMS y del Happiness Report. Aplicamos dropna() para eliminar registros incompletos que afectaban las métricas de salud. Finalmente, usamos sort_values() para crear los rankings de los países con mayor y menor expectativa de vida, filtrando los "Top 30" y "Bottom 30" para nuestros gráficos interactivos.

2. Agrupamiento Estratégico [groupby()]:
•	¿Para qué sirve? Pasa del análisis de filas individuales al análisis de segmentos de negocio. Agrupa los datos según una variable categórica (como países, regiones o años) y permite calcular métricas agregadas (sumas totales, promedios, conteos) para comparar el rendimiento entre distintos grupos.
•	Nuestra aplicación en el proyecto: Lo implementamos para agrupar los datos globales por continentes (Region). Gracias a esto, pudimos calcular el promedio de PBI y de Esperanza de Vida a nivel regional, lo que nos permitió visualizar macroeconómicamente las disparidades entre distintos bloques geográficos, en lugar de analizar casi 200 países de forma aislada.

3. Integración de Datasets [merge()]:
•	¿Para qué sirve? Es la herramienta clave para unificar múltiples fuentes de información. Funciona cruzando dos bases de datos distintas a través de una columna que tengan en común (la "llave"), enriqueciendo el análisis al permitir cruzar variables que originalmente estaban separadas.
•	Nuestra aplicación en el proyecto: Fue fundamental para nuestro análisis central. Utilizamos merge() para unir el dataset de la OMS (que contenía métricas duras de salud y economía) con el World Happiness Report de 2015 (que contenía métricas de percepción social). Usamos la columna del nombre del país (Country) como llave de unión, logrando un único dataframe que nos permitió cruzar, por ejemplo, el PBI per cápita con el puntaje de felicidad.

4. Diseño de KPIs e Índices Propios (Scoring):
•	¿Para qué sirve? Un KPI (Key Performance Indicator) resume el rendimiento en un solo número. El modelado de Scoring va un paso más allá: permite evaluar y rankear elementos asignándoles distintos pesos (ponderación matemática) a múltiples variables, creando un índice propio que refleja el éxito o el riesgo según los criterios del analista.
•	Nuestra aplicación en el proyecto: En lugar de mirar variables sueltas, diseñamos dos modelos matemáticos propios:
1.	Score de Riesgo Sanitario: Aislamos factores epidemiológicos (como tasas de Polio, Difteria y Hepatitis) para rankear qué países tenían los sistemas de inmunización más vulnerables.
2.	Score de Bienestar Integral: Creamos un índice ponderado muy robusto que premia el impacto positivo de la Esperanza de vida (40% de peso), el PBI (30%) y la Educación (10%), mientras penaliza fuertemente las tasas de mortalidad y prevalencia del VIH (20%).

5. Modelado Predictivo (Regresión Lineal y Forecast):
•	¿Para qué sirve? Representa el salto del análisis descriptivo (qué pasó) al análisis predictivo (qué pasará). Utiliza algoritmos de Machine Learning para aprender el comportamiento histórico de los datos, trazar una tendencia matemática y estimar valores futuros, cuantificando la incertidumbre mediante métricas de precisión.
•	Nuestra aplicación en el proyecto: Importamos la librería Scikit-Learn y entrenamos un modelo de LinearRegression utilizando el historial económico de los países. A partir de esta tendencia, hicimos un Forecast para proyectar el crecimiento del PBI mundial hacia el año 2025. Además, calculamos métricas de validación como el R2 (R-cuadrado) y el Error Absoluto Medio (MAE) para demostrar la confiabilidad estadística de nuestra proyección macroeconómica.

6. Visualización Estratégica de Datos (Matplotlib, Seaborn y Plotly):
•	¿Para qué sirve? La visualización de datos es una herramienta analítica fundamental. Sirve para traducir relaciones numéricas complejas en formatos visuales intuitivos. Esto permite a los analistas y tomadores de decisiones identificar rápidamente tendencias, valores atípicos (outliers) y la fuerza de las correlaciones entre distintas variables (como salud y economía) que serían imposibles de detectar leyendo únicamente tablas de datos crudos.
•	Nuestra aplicación en el proyecto: Implementamos cuatro niveles de visualización para dar soporte a nuestras conclusiones:
1.	Análisis Bivariado (Matplotlib y Seaborn): Generamos gráficos de dispersión estáticos para comprobar visualmente la teoría económica (ej. cómo reacciona la esperanza de vida a medida que aumenta la escolaridad o el PBI).
2.	Evolución Temporal con Doble Eje Y (twinx): Diseñamos gráficos de líneas superpuestos para analizar la evolución histórica de variables con magnitudes completamente distintas (por ejemplo, contrastar años de vida vs. inversión en salud pública) sin distorsionar la escala visual.
3.	Visualización Interactiva (Plotly Express): Creamos gráficos de burbujas dinámicos cruzando el Happiness Score con la Esperanza de Vida, donde el tamaño de cada burbuja representa el peso económico (PBI) del país. Además, personalizamos el Hover (la etiqueta al pasar el mouse) inyectando HTML para mostrar las banderas nacionales de manera profesional.
4.	Visualización de Tendencias y Forecast (Gráfico Predictivo): Contrastamos visualmente la línea de datos históricos reales del PBI con la proyección futura hacia el año 2025 estimada por nuestro modelo de regresión. Esto permite traducir el pronóstico matemático de Machine Learning en un formato intuitivo, facilitando el análisis de la expectativa de crecimiento económico global.
5.	Rankings y Segmentación de Extremos [sort_values(), head()]: Utilizamos sort_values() combinado con head() para generar rankings precisos. Aislamos el "Top 10" y el "Top 30" de países con mayor Esperanza de Vida y mejor puntaje en el Happiness Score. Esto nos permitió limpiar el ruido visual en los gráficos (evitando saturar la pantalla con casi 200 países) y enfocar nuestras conclusiones estratégicas en los líderes mundiales.

#RESULTADOS Y ANÁLISIS VISUAL:
A continuación, se presentan los hallazgos fundamentales de la investigación, estructurados desde una visión macroeconómica global hasta la proyección de tendencias futuras.

1. El Panorama Global (Gráfico de Burbujas):
 
•	Título: Radiografía Global: Felicidad, Longevidad y Poder Económico.
•	Lectura Técnica: Gráfico de burbujas interactivo donde el eje X representa el Happiness Score, el eje Y la Esperanza de Vida, el tamaño de la burbuja indica el volumen del PBI y el color agrupa por región geográfica.
•	Insight Macroeconómico: Se observa una clara segmentación global. Las regiones de Europa Occidental y Norteamérica se concentran en el cuadrante superior derecho, demostrando que el alto volumen económico (burbujas grandes) es un catalizador fundamental para el desarrollo social. Por el contrario, los países del África Subsahariana se agrupan en el cuadrante inferior izquierdo, evidenciando una trampa de pobreza donde el bajo PBI limita severamente la infraestructura de salud pública y la percepción de bienestar.

2. Relaciones Causales (Gráficos de Dispersión)
En esta sección se analiza cómo diferentes variables demográficas y económicas impactan directamente en la longevidad de la población.

•	Título: El Impacto del Crecimiento Económico en la Longevidad.
•	Lectura Técnica: Gráfico de dispersión que contrasta el Producto Bruto Interno ajustado en miles (eje X) frente a la Esperanza de Vida (eje Y).
•	Insight Macroeconómico: El gráfico demuestra una curva de "rendimientos decrecientes". En las economías más pobres, pequeños aumentos en el PBI generan grandes saltos en la esperanza de vida. Sin embargo, una vez que un país alcanza un alto nivel de desarrollo, los aumentos adicionales de riqueza no se traducen linealmente en más años de vida, evidenciando que el PBI tiene un límite en su impacto biológico si no va acompañado de innovación médica.

•	Título: El Capital Humano como Motor de Desarrollo Sociosanitario.
•	Lectura Técnica: Gráfico de dispersión que correlaciona los años promedio de escolaridad formal (eje X) frente a la esperanza de vida (eje Y).
•	Insight Macroeconómico: Se observa una fuerte correlación lineal positiva que confirma la Teoría del Capital Humano. La educación fomenta la movilidad social, el acceso a mejores empleos y una mayor conciencia preventiva en salud. En términos económicos, una población educada no solo es más longeva, sino también más productiva para la matriz empresarial del país.

•	Título: El Costo Demográfico de la Mortalidad Prematura.
•	Lectura Técnica: Gráfico de dispersión que evalúa la relación inversamente proporcional entre las tasas de mortalidad infantil/adulta (eje X) y el promedio de esperanza de vida (eje Y).
•	Insight Macroeconómico: La estricta correlación negativa demuestra que la mayor "fuga de capital humano" en los países en vías de desarrollo ocurre en los primeros años de vida. Reducir la mortalidad infantil mediante políticas preventivas de bajo costo es la inversión estatal con el Retorno sobre la Inversión (ROI) social más alto para empujar el promedio de longevidad hacia arriba.

•	Título: Impacto Epidemiológico en el Estancamiento Demográfico.
•	Lectura Técnica: Gráfico de dispersión que vincula la prevalencia de VIH/SIDA (eje X) con la caída de la esperanza de vida (eje Y).
•	Insight Macroeconómico: Se evidencia un shock sanitario masivo, particularmente focalizado en naciones africanas, donde la esperanza de vida colapsa frente a altas tasas de infección. A nivel macroeconómico, este factor destruye la Población Económicamente Activa (PEA), generando un círculo vicioso de baja productividad, pérdida de mano de obra y una presión fiscal insostenible sobre la salud pública.

3. Casos de Éxito y Zonas Críticas (Rankings)
(Pegar aquí la tabla o el gráfico de barras del Top 10. Creo que por el momento todavía lo tenemos en TOP 30)
•	Título: Benchmarking Internacional: Líderes y Rezagados en Eficiencia.
•	Lectura Técnica: Segmentación de los extremos de la distribución (Top 10 y Bottom 10) calculados a partir de nuestro Score de Bienestar Integral y el Score de Riesgo Sanitario.
•	Insight Macroeconómico: El ranking de líderes no está dominado exclusivamente por los países con mayor PBI bruto, sino por aquellos que presentan la mayor eficiencia en la asignación de sus recursos, transformando riqueza en salud y educación. Por el contrario, la base del ranking refleja naciones penalizadas severamente por fallas en el control epidemiológico, lo que estanca su crecimiento económico.



4. Evolución Temporal y Eficiencia Estatal (Caso Argentina)
Mediante gráficos de doble eje Y, se audita la evolución del bienestar social frente al desempeño institucional y económico del país.
 
•	Título: Resiliencia Sanitaria frente a la Volatilidad Macroeconómica.
•	Lectura Técnica: Gráfico de líneas con doble escala. La línea azul marca la Esperanza de Vida (eje izquierdo), y la línea punteada verde traza la evolución del PBI (eje derecho).
•	Insight Macroeconómico: Permite observar la "asimetría temporal" entre economía y demografía. Las crisis y caídas del PBI en Argentina no provocan desplomes automáticos en la esperanza de vida. Esto sugiere que la infraestructura de salud instalada previamente funciona como un amortiguador social, sosteniendo la longevidad a pesar de los ciclos recesivos.
 
•	Título: Análisis de Eficiencia del Gasto Público en Salud.
•	Lectura Técnica: Contraste de la Esperanza de Vida (eje izquierdo) con el Gasto en Salud medido como porcentaje del gasto total del Estado (eje derecho).
•	Insight Macroeconómico:……………...
 
•	Título: Efecto Compuesto de la Inversión Institucional a Largo Plazo.
•	Lectura Técnica: Superposición de la tendencia de la Esperanza de Vida (eje izquierdo) con el crecimiento de los años promedio de Escolaridad (eje derecho).
•	Insight Macroeconómico: El crecimiento paralelo de ambas líneas confirma el efecto compuesto de las políticas de Estado. A medida que nuevas generaciones ingresan al mercado con mayor escolaridad formal, sus mejores condiciones de empleabilidad elevan estructuralmente el piso de esperanza de vida a nivel nacional, blindando a la población contra la pobreza.


5. Proyección Estratégica (Forecast)
•	Sesgos detectados: Los datos analizados corresponden principalmente al año 2015. El análisis predictivo asume condiciones estables, por lo que shocks globales no previstos (como la pandemia del COVID-19 o crisis geopolíticas) actúan como sesgos que alterarían las tendencias calculadas por el modelo histórico.
 
•	Título: Proyección Macroeconómica: Evolución del PBI Global hacia 2025.
•	Lectura Técnica: Gráfico de tendencias que superpone los datos históricos reales del PBI con la recta predictiva generada por nuestro modelo de Regresión Lineal proyectada hacia la próxima década.
•	Insight Macroeconómico: El modelo estadístico confirma una tendencia de base alcista para la economía global, sustentada por un alto nivel de precisión métrica (R2). Sin embargo, desde una óptica de planificación estratégica, este escenario "Base" asume una continuidad histórica y deberá ser ajustado ante potenciales shocks externos (como crisis financieras o coyunturas pandémicas) que puedan alterar la pendiente de crecimiento proyectada por el algoritmo.

#RESULTADOS DESTACADOS:

IDEA TEMPORAL (Le dije a la IA que hiciera una. Luego hago una conclusión)
A través de la integración y modelado de datos sociodemográficos y económicos globales, este proyecto demuestra empíricamente que la riqueza nacional (PBI) es una condición necesaria, pero no suficiente, para garantizar el bienestar integral de la población.
Los hallazgos clave de nuestro análisis revelan que:
•	El desarrollo tiene rendimientos decrecientes: El impacto del crecimiento económico en la esperanza de vida es masivo en etapas iniciales de desarrollo (logrando sacar a poblaciones de la pobreza extrema), pero se estabiliza en economías avanzadas si no se acompaña de políticas de salud eficientes.
•	El Capital Humano es el verdadero motor: La inversión sostenida en educación (Escolaridad) demostró tener una correlación directa y estructural con la longevidad, actuando como un escudo protector frente a la volatilidad macroeconómica (como se observó en el caso de Argentina).
•	La eficiencia estatal salva vidas: Nuestros modelos de Scoring confirmaron que los países líderes no son exclusivamente los de mayor PBI bruto, sino aquellos que logran traducir su presupuesto en un control epidemiológico efectivo y en la reducción de la mortalidad prematura.
Finalmente, aunque nuestro modelo predictivo (Forecast) proyecta un escenario base de crecimiento económico global continuo hacia 2025, el desafío real para los tomadores de decisiones será utilizar el análisis de datos para asegurar que dicha expansión financiera se convierta en eficiencia sanitaria, resiliencia demográfica y felicidad real.

