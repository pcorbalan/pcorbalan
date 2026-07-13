# Pablo Nicolás Corbalán

**Ecólogo y Analista Geoespacial**

Licenciado en Ecología y Conservación del Ambiente (UNSE) | Doctorando en Ciencias Biológicas (UNC)

---

## Sobre mí

Soy ecólogo con una fuerte orientación hacia el análisis geoespacial y la teledetección. Me apasiona entender cómo cambia el paisaje a lo largo del tiempo y qué consecuencias tiene eso para el ciclo del carbono.

Actualmente estoy desarrollando mi doctorado en el Chaco Seco argentino, una de las ecorregiones con mayor tasa de deforestación del mundo. Mi proyecto busca responder una pregunta concreta: ¿cómo afectan las distintas trayectorias de uso del suelo al balance de carbono de un territorio? Y más importante aún: ¿podemos predecir cuánto carbono puede capturar un lote en función de su historia de uso?

Para eso combino series temporales satelitales, algoritmos de aprendizaje automático y modelado geoespacial, todo implementado en Google Earth Engine.

A largo plazo, me interesa aplicar este conocimiento en los mercados de carbono voluntarios, donde la cuantificación rigurosa del carbono es clave, y desarrollar herramientas accesibles que permitan a productores y gestores ambientales tomar decisiones informadas sobre sus territorios.

---

## Doctorado

**"Trayectorias de uso del suelo y dinámica del carbono en el Chaco Seco: implicancias para el balance y la captura de carbono"**
*Universidad Nacional de Córdoba — Doctorado en Ciencias Biológicas*
Director: Dr. Hugo Zerda

| Etapa | Descripción | Datos | Herramientas |
|---|---|---|---|
| **Año 1 — Clasificación** | Mapas anuales de uso del suelo 2000–2024 reclasificados a 5 clases funcionales orientadas al carbono (bosque nativo, arbustal, agricultura, suelo desnudo, agua) a partir de MapBiomas Argentina | MapBiomas Argentina Col. 2 · Landsat 5/8/9 | Google Earth Engine · QGIS |
| **Año 2 — Trayectorias** | Construcción de trayectorias multitemporales píxel a píxel (30m). Identificación de patrones de cambio: deforestación, abandono, regeneración, intensificación agrícola. Análisis espacial de hotspots y patrones regionales | Mapas anuales Año 1 | Python · GeoPandas · GEE |
| **Año 3 — Balance de carbono** | Estimación del balance de carbono por trayectoria integrando biomasa aérea, variables climáticas, edáficas y topográficas. Validación con parcelas permanentes del IER. Enfoque stock-change: ΔC = C_t2 − C_t1 | GEDI · MODIS · SoilGrids · Parcelas IER | Python · XGBoost · Random Forest |
| **Año 4–5 — Herramienta GEE** | Modelos predictivos de captura futura de carbono bajo distintos escenarios. Desarrollo de una herramienta operativa en GEE que permita estimar el balance y el potencial de captura a escala predial, con escalamiento regional | Resultados Años 1–3 | GEE App · XGBoost · Redes neuronales |

---

## Herramientas y tecnologías

**Teledetección y SIG**
Google Earth Engine · QGIS · Landsat · Sentinel-1/2 · MODIS · GEDI · MapBiomas

**Programación**
Python · JavaScript (GEE API)

**Librerías Python**
GeoPandas · Rasterio · Pandas · NumPy · Matplotlib

**Métodos**
Clasificación supervisada · Análisis espaciotemporal · Machine learning · Modelado de carbono

---

## Aspiraciones

Me gustaría contribuir al desarrollo de herramientas concretas que permitan estimar el balance de carbono y el potencial de captura a escala predial, aplicables tanto en contextos de planificación territorial como en proyectos de mercados de carbono voluntarios.

El producto final de mi doctorado es una aplicación en Google Earth Engine donde un usuario puede ingresar un lote o área de interés y obtener estimaciones del balance histórico de carbono y predicciones de captura futura en función de sus trayectorias de uso del suelo. Eso tiene aplicaciones directas en REDD+, VCS y otros estándares del mercado de carbono.

A futuro me interesa trabajar en consultoría ambiental o en empresas del sector de carbono, aportando la combinación de conocimiento ecológico, capacidad de análisis geoespacial y manejo de herramientas de machine learning aplicadas al territorio.

---

## Contacto

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Pablo_Corbalán-0077B5?style=flat&logo=linkedin)](https://www.linkedin.com/in/pablo-corbalan-34982b2ba/)
[![Email](https://img.shields.io/badge/Email-pablocorbalan9898@gmail.com-D14836?style=flat&logo=gmail)](mailto:pablocorbalan9898@gmail.com)

📍 Santiago del Estero, Argentina
