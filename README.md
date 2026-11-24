# Taller "El Barista Novato y el Manager" (IA agéntica)

Introducción a sistemas multiagente con el patrón **Reflexión / Crítico**
(self-correction) en Red Hat Openshift AI: un agente genera una respuesta, y otro la evalúa y devuelve un
JSON. El código Python repite el ciclo (como mucho 3 veces) hasta que el
crítico la aprueba.



| Archivo | Para qué |
|---|---|
| `barista-y-manager.ipynb` | El notebook de los participantes (retos con `TODO` + soluciones desplegables) |

## Estructura del notebook

| Sección | Qué hacen los asistentes |
|---|---|
| 0. Preparación | Se les da `llamar_modelo(system, user)` ya hecha |
| 1. Barista | **Reto 1:** inyectar el feedback y el borrador anterior en el prompt |
| 2. Manager | **Reto 2:** leer el JSON de forma robusta y *fail-closed* (tests sin LLM) |
| 3. Orquestación | **Reto 3:** el bucle generar → evaluar → corregir, con límite y respuesta de reserva |
| 4. Varios pedidos | Tasa de aprobación, número de intentos y coste en llamadas/tokens |
| 5. ¿Quién vigila al vigilante? | Juez LLM frente a regla determinista, inyección de prompt contra el manager |
| 6. Retos extra | Guided decoding (`guided_json`), tercer agente, historial acumulado, temperatura... |



## Preparación en RHOAI

1. **Workbench:** en el dashboard de OpenShift AI → seleccionar el workbench que aparece disponible.
2. Clonar este repositorio en el workbench.
3. Por defecto el notebook busca el modelo en
   `http://llama-32-predictor.<namespace-del-workbench>.svc.cluster.local:8080/v1`.
   Si el workbench está en otro namespace o el modelo es externo, definid
   `LLM_URL`, `LLM_MODEL` y `LLM_API_KEY` como variables de entorno del workbench
   (o editad la celda de configuración).


