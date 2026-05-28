#  Estrategia de Retención Inteligente: Predicción de Churn en Telecomunicaciones

Este proyecto presenta una solución integral de Ciencia de Datos para reducir la tasa de abandono de clientes (**Churn**) en una compañía de telecomunicaciones. A través de un análisis proactivo y modelos predictivos, transformamos datos históricos en estrategias de negocio accionables.

##  El Desafío del Negocio
La compañía presentaba una tasa de abandono del **26.5%**. El objetivo principal fue identificar los factores críticos de fuga y desarrollar un motor de decisión que permitiera intervenir antes de la pérdida definitiva del cliente.

##  Hallazgos Clave (Análisis de Datos)
Tras auditar el comportamiento de los clientes, identificamos los 6 "puntos de dolor" que disparan la salida:

1.  **Sensibilidad al Precio (KDEPlot):** Existe una correlación directa: los clientes que más pagan tienen una mayor probabilidad de fuga. El servicio se percibe como un gasto pesado.
2.  **El "Valle de la Muerte" (Meses 6-10):** El riesgo máximo de abandono ocurre en este periodo, especialmente en contratos "mes a mes". Los contratos anuales actúan como un escudo protector.
3.  **La Trampa de la Fibra Óptica:** A pesar de ser el producto premium, los clientes de Fibra son los más propensos a la fuga, sugiriendo fallos en la relación calidad-precio.
4.  **Fricción Digital (33.6% Churn):** Los usuarios de factura digital (*Paperless Billing*) se van el doble que los de factura física.
5.  **Barrera del Pago Manual:** El uso de *Electronic Check* genera fricción mensual. Los métodos de pago automáticos retienen significativamente más.
6.  **Servicios "Ancla" Ausentes:** La falta de servicios de Seguridad Online y Soporte Técnico duplica el riesgo de abandono.

##  Comparativa de Modelos y Optimización
Se evaluaron diversos algoritmos, destacando la importancia de la **limpieza manual de variables** (Inteligencia de Negocio) sobre la selección automática (RFE).

| Modelo / Iteración | Exactitud | F1-Score | Precisión | Recall |
| :--- | :---: | :---: | :---: | :---: |
| Random Forest (Base) | 77.64% | 0.6307 | 56.16% | 71.93% |
| Regresión Logística (Manual) | 74.73% | 0.6261 | 51.56% | 79.68% |
| **Regresión Logística (Umbral 0.60)** | **78.14%** | **0.6393** | **56.87%** | **72.99%** |

**Modelo Ganador:** Se seleccionó la **Regresión Logística con Umbral 0.60** por su equilibrio perfecto entre precisión y capacidad de detección, minimizando costos operativos por falsas alarmas.

##  El "Telco Playbook": Estrategias de Retención
Propuestas de intervención basadas en los hallazgos:

* **Auditoría de Valor "Fibra 360":** Ajuste proactivo de planes para clientes de alto valor en zonas competitivas.
* **Programa "Puente de Lealtad":** Incentivar el paso de contrato mensual a anual en el mes 8 con beneficios de velocidad.
* **Ecosistema "Tranquilidad Total":** Bundle gratuito de seguridad y soporte técnico a cambio de contratos de 24 meses.
* **Incentivo "Click & Forget":** Descuentos permanentes (3%) por migrar a pagos automáticos.
* **Plan "Hogar Conectado":** Beneficios familiares para aumentar el costo psicológico de cancelación.

##  Tecnologías Utilizadas
* **Python 3.x**
* **Pandas & Numpy:** Manipulación de datos.
* **Scikit-Learn:** Modelado predictivo y preprocesamiento.
* **Matplotlib & Seaborn:** Visualización avanzada (KDEPlots, Matrices de Confusión).
* **Joblib:** Serialización del modelo.

##  Cómo usar el modelo
El modelo final está serializado en `models/modelo_retencion_final.pkl`. Puedes cargarlo de la siguiente manera:

```python
import joblib
modelo = joblib.load('models/modelo_retencion_final.pkl')
# El modelo incluye el preprocesamiento y el umbral de 0.60
predicciones = modelo.predict(nuevos_datos)
