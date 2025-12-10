# Forecast de Ventas — Proyecto End-to-End

**Nombre del proyecto:** Forecast de Ventas por Tienda y Producto  
**Autor:** Hugo Cruz  
**Rol demostrado:** Analista de Datos / Data Scientist (end-to-end)

---

## 1. Objetivo de negocio (Executive summary)
Predecir las ventas futuras (por semana) a nivel **tienda x producto** para optimizar inventarios, reducir quiebres de stock y mejorar la planificación comercial. El proyecto traduce predicciones en acciones concretas (reabastecimiento, promociones, reasignación de stock) con impacto medible en servicio al cliente y costos de inventario.

---

## 2. Propósito del trabajo
- Demostrar un flujo analítico completo: **adquisición y limpieza de datos → EDA → feature engineering → modelado predictivo → evaluación → visualización y recomendaciones de negocio**.
- Entregar artefactos reproducibles (notebooks, scripts, dashboard y slides) que permitan a un equipo productivo ejecutar y validar el trabajo.
- Mostrar capacidad para justificar decisiones técnicas y medir impacto comercial.

---

## 3. Preguntas de negocio que responde
1. ¿Cuáles serán las ventas estimadas para la próxima semana/mes por tienda y por producto?  
2. ¿Qué tiendas/productos presentan mayor riesgo de stockout según el forecast?  
3. ¿Qué reducción esperada de quiebres de stock o excesos de inventario se puede obtener actuando sobre las recomendaciones?  
4. ¿Qué features (promociones, estacionalidad, días festivos, clima) afectan más la demanda?

---

## 4. Entregables (artifacts)
- `notebooks/00-EDA.ipynb` — Análisis exploratorio completo.  
- `notebooks/01-feature-engineering.ipynb` — Ingeniería de features (lags, rolling stats, variables calendario).  
- `notebooks/02-modeling.ipynb` — Modelos comparativos (Baseline, ARIMA/Prophet, XGBoost) + validación.  
- `notebooks/03-reporting.ipynb` — Reporting y evaluación final.  
- `src/` — Scripts reproducibles (`extract.py`, `transform.py`, `train.py`, `predict.py`).  
- `dashboard/` — Export del dashboard (.twbx / capturas) con visualizaciones clave.  
- `slides/` — Deck (6–8 diapositivas) para presentar a stakeholders.  
- `README.md` (este archivo) con reproducción y criterios de aceptación.  
- `requirements.txt` — Dependencias necesarias.

---

## 5. Dataset (origen y notas)
- Origen sugerido: Kaggle / datos públicos de retailers o dataset simulado/anonimizado si no hay acceso a datos reales.  
- Columnas típicas esperadas:
  - `date` (YYYY-MM-DD)
  - `store_id`
  - `product_id`
  - `sales` (cantidad o revenue)
  - `price` (si disponible)
  - `promo_flag` (0/1)
  - `stock` (opcional)
  - variables externas opcionales: `holiday_flag`, `weather_indicators`
- Notas: No subir datos sensibles. Incluir script para regenerar o mostrar sample de `data/processed/` para reproducibilidad.

---

## 6. Metodología (resumen)
1. **Ingesta & limpieza:** unificar formatos, tratar missing, remover outliers justificando criterios.  
2. **EDA temporal:** descomposición de series (trend/seasonality), autocorrelación, visualización por tienda/producto.  
3. **Feature engineering:** lags (1,7,30), rolling means, day-of-week, month, is_holiday, promo windows.  
4. **Validación temporal:** data split por tiempo (train / val / test), backtesting con ventanas deslizantes.  
5. **Modelado:** baseline naive; modelos clásicos (SARIMA/Prophet) y modelos de machine learning (XGBoost, LightGBM) con features de lags.  
6. **Evaluación:** RMSE, MAE, MAPE por horizon y por tienda/producto; análisis de residuals y errores por segmento.  
7. **Deployment-ready prototyping:** pipeline minimal para scoring (script `predict.py`) y pseudocódigo de integración en sistema de inventario.

---

## 7. Métricas de éxito (KPIs del proyecto)
- **Primarias:** RMSE (por horizonte), MAE, MAPE.  
- **Operacionales (estimadas / caso de negocio):** reducción esperada de stockouts (%), reducción de excesos de inventario (%), mejora en fill-rate.  
- **Calidad del modelo:** estabilidad de error en backtests, importancia de features, robustez ante promociones.

---

## 8. Habilidades técnicas demostradas en este proyecto
- Ingeniería de datos y ETL (SQL + Python).  
- Análisis exploratorio y visualización de series temporales.  
- Feature engineering avanzado para series temporales.  
- Modelado predictivo: SARIMA/Prophet y modelos basados en árboles (XGBoost/LightGBM).  
- Validación temporal y backtesting.  
- Evaluación de modelos con métricas relevantes de negocio.  
- Preparación de dashboards (Tableau / Power BI) y storytelling para stakeholders.  
- Buenas prácticas de reproducibilidad: scripts, requirements y README.

---

## 9. Estructura de archivos (esperada)
