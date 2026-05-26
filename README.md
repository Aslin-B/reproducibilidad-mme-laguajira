# Paquete de reproducibilidad — AG-0.9-2026

**Estudio:** Aprendizaje automático interpretable para estratificar el riesgo de eventos adversos materno-perinatales en La Guajira (Colombia), 2016–2022.

**Revista destino:** Revista Facultad Nacional de Salud Pública, Universidad de Antioquia.

Este paquete reúne todo lo necesario para replicar los análisis cuantitativos del manuscrito y para sustentar las guías RECORD y CAIR que solicitaron los pares evaluadores.

---

## Contenido de la carpeta

| Archivo | Tipo | Propósito |
|---|---|---|
| `colab_replicabilidad_MME_LaGuajira.ipynb` | Notebook Jupyter | Programa principal para ejecutar en Google Colab. Reproduce paso a paso todos los análisis y figuras del artículo. |
| `dataset_MME_LaGuajira_2016_2022.xlsx` | Excel | Dataset anonimizado del Sivigila (5 706 filas × 13 columnas) con tres hojas: datos, diccionario de variables y metadata. |
| `checklist_RECORD_diligenciado.docx` | Word | Checklist RECORD (29 ítems) completamente diligenciado para sustentar transparencia en datos rutinarios. |
| `checklist_CAIR_diligenciado.docx` | Word | Checklist CAIR (31 ítems, Olczak *et al.* 2021) completamente diligenciado para el componente de inteligencia artificial. |
| `README.md` | Texto | Este documento. |

---

## Cómo ejecutar el notebook en Google Colab

### Opción A — Subir el notebook a Colab manualmente

1. Abrir [colab.research.google.com](https://colab.research.google.com).
2. Menú `Archivo` → `Subir cuaderno` → seleccionar `colab_replicabilidad_MME_LaGuajira.ipynb`.
3. Ejecutar la primera celda (instala dependencias en ~30 segundos).
4. Cuando el notebook lo solicite (Paso 4), subir el archivo `dataset_MME_LaGuajira_2016_2022.xlsx`.
5. Menú `Entorno de ejecución` → `Ejecutar todo`. El cuaderno completo tarda entre tres y cinco minutos.

### Opción B — Publicar en GitHub y abrir desde allí

1. Subir todos los archivos de esta carpeta a un repositorio de GitHub.
2. Cualquiera puede abrir el notebook directamente pegando la URL en Colab: `https://colab.research.google.com/github/<usuario>/<repo>/blob/main/colab_replicabilidad_MME_LaGuajira.ipynb`.
3. Útil para incluir el enlace permanente en el manuscrito como material complementario.

### Opción C — Ejecución local

El notebook también funciona en Jupyter local. Requiere Python 3.10+ y las dependencias listadas en la primera celda. El único cambio necesario es reemplazar la celda de carga de archivos (`google.colab.files.upload`) por una lectura directa con `pd.read_excel`.

---

## Estructura del notebook (39 celdas)

| Paso | Contenido |
|---|---|
| 1–3 | Instalación de dependencias, importación de librerías, configuración visual con paleta Okabe-Ito. |
| 4 | Carga del dataset Excel (con diálogo interactivo). |
| 5 | Análisis exploratorio: estructura, faltantes, distribución del desenlace, descriptivas. |
| 6 | Preprocesamiento: imputación, separación X/y. |
| 7 | Análisis bivariado (chi-cuadrado y U de Mann-Whitney). |
| 8–9 | Regresión logística multivariada con OR e IC 95 % y forest plot (Figura 5 del artículo). |
| 10 | Comparación sistemática de ocho algoritmos con validación cruzada estratificada y SMOTE. |
| 11 | Figura 2: AUC con IC 95 % de los ocho modelos. |
| 12 | Figura 3: importancia de variables por permutación. |
| 13 | Figura 4: curvas ROC y precisión-recall de los cuatro mejores modelos. |
| 14 | Matriz de confusión del modelo ganador. |
| 15 | Descarga de las figuras generadas como archivo ZIP. |

Cada celda de código está comentada línea por línea. Cada celda de código va precedida por una celda Markdown que explica el qué, el cómo y el porqué de la operación, alineado con las guías RECORD y CAIR.

---

## Resultados esperados de la replicación

| Resultado | Valor en el artículo |
|---|---|
| Tamaño de la cohorte MME | 5 706 notificaciones |
| Prevalencia MME severa | 4,45 % |
| AUC Random Forest | 0,73 (IC 95 %: 0,69–0,77) |
| AUC Gradient Boosting | 0,72 |
| AUC XGBoost | 0,71 |
| AUC Reg. logística | 0,65 |
| Variable más informativa | Tipo de terminación de la gestación |
| OR pertenencia indígena | 1,72 (IC 1,26–2,34); p = 0,001 |
| OR controles prenatales insuficientes | 1,48 (IC 1,12–1,94); p = 0,005 |
| OR edad ≥ 35 años | 0,65 (IC 0,43–0,99); p = 0,046 |

Si la ejecución reproduce estos valores (con tolerancia de ± 0,005 por aleatoriedad numérica), la replicación es exitosa.

---

## Documentos de transparencia

### Checklist RECORD

La extensión RECORD de STROBE para estudios sobre datos rutinarios de salud agrega siete ítems específicos (6.1, 6.2, 6.3, 7.1, 12.1, 12.2, 12.3, 13.1, 19.1, 22.1) que sustentan la trazabilidad del proceso de selección, vinculación, validación y reporte. El archivo `checklist_RECORD_diligenciado.docx` cubre los 29 ítems con la ubicación precisa de cada respuesta en el manuscrito AG-0.9-2026.

### Checklist CAIR

El checklist CAIR (Clinical Artificial Intelligence Research, Olczak *et al.* 2021) organiza la información en seis dominios: (i) pregunta clínica y antecedentes, (ii) datos y preparación, (iii) modelo y arquitectura, (iv) validación y desempeño, (v) interpretabilidad y consideraciones clínicas, y (vi) consideraciones éticas y prácticas. El archivo `checklist_CAIR_diligenciado.docx` cubre los 31 ítems.

**Referencia obligatoria:**

> Olczak J, Pavlopoulos J, Prijs J, Ijpma FFA, Doornberg JN, Lundström C, Hedlund J, Gordon M. Presenting artificial intelligence, deep learning, and machine learning studies to clinicians and healthcare stakeholders: an introductory reference with a guideline and a Clinical AI Research (CAIR) checklist proposal. *Acta Orthop.* 2021 Oct;92(5):513-525. DOI: [10.1080/17453674.2021.1918389](https://doi.org/10.1080/17453674.2021.1918389)

---

## Consideraciones éticas y legales

- **Anonimización:** El dataset no contiene identificadores directos (ID, nombres, direcciones, fechas exactas, códigos municipales finos). Cumple con la Ley 1581 de 2012 de protección de datos personales de Colombia.
- **Aval ético:** Comité Institucional de Ética en Investigación, Universidad de La Guajira, acta n.° 04 del 12 de marzo de 2023. Estudio clasificado como investigación sin riesgo (Resolución 8430 de 1993, art. 11).
- **Uso permitido:** Investigación académica con citación al manuscrito AG-0.9-2026 y reconocimiento al Instituto Nacional de Salud de Colombia como fuente original de los datos.
- **Uso no permitido:** Re-identificación de personas, comercialización, integración con bases que permitan la re-identificación.

---

## Cita sugerida

> Botello-Plata AG, Uribe-Orrego M, Ramírez-Cardeño W. Aprendizaje automático interpretable para estratificar el riesgo de eventos adversos materno-perinatales. *Revista Facultad Nacional de Salud Pública.* Universidad de Antioquia; en evaluación, 2026. Manuscrito 361736.

---

## Contacto y soporte técnico

Para preguntas sobre la replicación del análisis o sobre el dataset, contactar a los autores a través del sistema OJS de la Revista Facultad Nacional de Salud Pública.

---

*Paquete preparado siguiendo los lineamientos de transparencia y reproducibilidad de la RFNSP y las guías STROBE, RECORD, TRIPOD-AI, CAIR y SRQR.*
