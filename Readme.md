# Credit-Card Fraud Detection · MLOps-Ready Project

![Project Banner](https://via.placeholder.com/800x200?text=Credit+Card+Fraud+Detection+%7C+MLOps)  
*Reemplaza con tu banner real*

---

## 📌 Descripción general  
Proyecto para detectar transacciones fraudulentas de tarjetas de crédito y demostrar un flujo **MLOps end-to-end** (ingesta → entrenamiento → despliegue → monitoreo). Incluye CI/CD, contenedorización, orquestación en Kubernetes y control de experimentos con MLflow para asegurar reproducibilidad y escalabilidad en producción.

---

## 🔍 Funcionalidades clave
| Categoría           | Descripción                                                                      |
|---------------------|----------------------------------------------------------------------------------|
| **Detección ML**    | Modelos de clasificación con ajuste de hiper-parámetros y manejo de desbalanceo. |
| **Pipeline CI/CD**  | GitHub Actions / Jenkins ejecutan `run_full_pipeline.sh` con tests automáticos.   |
| **Container Ready** | `Dockerfile` empaqueta `api_app.py` + dependencias para despliegue portable.      |
| **Kubernetes**      | `kubernetes_manifests.yaml` define *Deployment*, *Service* y *HPA* auto-escalable.|
| **Tracking MLflow** | Directorio `mlruns/` almacena métricas, artefactos y versiones de modelo.         |
| **Monitoreo**       | `monitor_model_performance.py` publica latencia, *drift* y métricas a Prometheus. |
| **Tests**           | Suite `tests/` (pytest) valida datos, entrenamiento y API REST.                  |

---

## 🛠️ Tech-Stack
- **Python 3.10** · ML core  
- **Scikit-learn, XGBoost, PyTorch** · Modelos  
- **Pandas / NumPy** · Procesamiento  
- **MLflow** · Experiment tracking & model registry  
- **Docker + Kubernetes** · Despliegue escalable  
- **GitHub Actions / Jenkins** · CI/CD  
- **Prometheus + Grafana** · Monitoreo  
- **Flask RESTX** · Inference API  
- **Great Expectations** · Validación de datos  

---

## 📊 Dataset  
[Kaggle Credit-Card Fraud Detection](https://www.kaggle.com/mlg-ulb/creditcardfraud)  
- **284 807** transacciones  
- **492** fraudes (0.17 % → dataset altamente desbalanceado)  
- **30** variables PCA + `Amount`, `Time`

---

## 🧠 Flujo de Machine Learning

```bash
# Orquestado por scripts/bash o por el pipeline CI:
./scripts/run_full_pipeline.sh
```

1. **Preprocesado** → `src/preprocessing/`  
2. **Ingeniería de características** → `data/features_v1.json`  
3. **Entrenamiento + HPO** → `src/training/` (MLflow autolog)  
4. **Evaluación / Sesgo** → `src/evaluation/`  
5. **Registro de modelo** → `models/fraud_model_v1.pkl` & `mlruns/`  
6. **Empaquetado Docker** → `deployment/Dockerfile`  
7. **Despliegue K8s** → `deployment/kubernetes_manifests.yaml`  
8. **Monitoreo** → Prometheus exporter en `scripts/monitor_model_performance.py`

---

## 📈 Métricas de referencia (v 1.0)
| Métrica   | Valor |
|-----------|-------|
| Precision | 0.93  |
| Recall    | 0.87  |
| F1-Score  | 0.90  |
| ROC-AUC   | 0.98  |

*Actualiza con los valores reales de `model_metrics_v1.json`.*

---

## 🚀 Primeros pasos

```bash
# 1 · Clonar el repo
git clone https://github.com/yourusername/credit-card-fraud-mlops.git
cd credit-card-fraud-mlops

# 2 · Crear entorno
python -m venv .venv && source .venv/bin/activate
pip install -r requirements.txt

# 3 · Ejecutar pipeline local completo
bash scripts/run_full_pipeline.sh
```

### Despliegue en K8s (requiere Docker & kubectl configurados)

```bash
docker build -t fraud-api:latest -f deployment/Dockerfile .
kubectl apply -f deployment/kubernetes_manifests.yaml
```

---

## 📂 Estructura del proyecto
```text
.
├── Projecto_Detección_de_fraude.ipynb
├── README.md
├── data
│   ├── cleaned_data.parquet
│   ├── data_schema.json
│   ├── features_v1.json
│   └── raw_transactions.csv
├── deployment
│   ├── Dockerfile
│   ├── cicd_config.yaml
│   └── kubernetes_manifests.yaml
├── mlruns/
├── models
│   ├── fraud_model_v1.pkl
│   ├── model_config.json
│   └── model_metrics_v1.json
├── notebooks
│   ├── 01_EDA_initial_analysis.ipynb
│   ├── 02_model_experimentation.ipynb
│   └── 03_pipeline_prototyping.ipynb
├── requirements.txt
├── scripts
│   ├── monitor_model_performance.py
│   ├── run_full_pipeline.sh
│   └── train_deploy_pipeline.py
├── src
│   ├── evaluation/
│   ├── features/
│   ├── preprocessing/
│   ├── serving/
│   └── training/
└── tests/
```

---

## 🤝 Contribuir
1. Haz **fork** del proyecto  
2. Crea tu rama de funcionalidades  
   ```bash
   git checkout -b feature/MiFeature
   ```  
3. Haz commits significativos  
   ```bash
   git commit -m "Añade mi feature"
   ```  
4. Envía la rama a tu fork  
   ```bash
   git push origin feature/MiFeature
   ```  
5. Abre un **Pull Request** en el repositorio principal

---

## 📜 Licencia  
Distribuido bajo la **MIT License**. Consulta `LICENSE`.

---

## 📧 Contacto  
**Tu Nombre** — palciosdata.tec
Repo: <https://github.com/EnriquePalacios99/Projecto_Detecci-n_de_fraude_en_tarjetas_de_cr-dito>
