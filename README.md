# clasificacion-ML


# Proyecto de Predicción de Incumplimiento de Pagos

Este proyecto de clasificación predice si un cliente incumplirá el pago de su tarjeta de crédito utilizando técnicas de Machine Learning.

## Estructura del Proyecto
- **Notebook-1.ipynb**: Análisis exploratorio de los datos.
- **Notebook-2.ipynb**: Selección de características y prueba de múltiples algoritmos con Lazy Predict.
- **TNotebook-3**: Entrenamiento del mejor modelo y registro en MLFlow.

## Requisitos
1. Python 3.7 o superior.
2. Instalar las dependencias del archivo `requirements.txt`.

## Cómo ejecutar
1. Clonar el repositorio.
2. Crear un entorno virtual en Python con el commando: python3 -m venv venv
3. Activar el entorno virtual: source venv/bin/activate
4. Instalar las dependencias: `pip install -r requirements.txt`.
6. Instalar Jupyter Notebook: pip install notebook
5. Abrir jupyter: jupyter notebook
3. Ejecutar los notebooks en el orden descrito
4. Visualizar los resultados y los registros en MLFlow.

## Solución de problemas

### XGBoostError: XGBoost Library (libxgboost.dylib) could not be loaded
Solución: 
Instala OpenMP usando Homebrew:

brew install libomp
Verifica que OpenMP está instalado. Puedes verificar que libomp.dylib está en el lugar correcto:

ls /opt/homebrew/opt/libomp/lib/libomp.dylib
Deberías ver la biblioteca listada en la salida.

Reinstala XGBoost para asegurarte de que está correctamente configurado para usar OpenMP:

pip install xgboost

### TypeError: OneHotEncoder.init() got an unexpected keyword argument 'sparse'
Solución:
Abre el archivo Supervised.py en el directorio de instalación de LazyPredict. La ruta debería ser algo similar a /Library/Frameworks/Python.framework/Versions/3.12/lib/python3.12/site-packages/lazypredict/Supervised.py.

Reemplaza sparse=False con sparse_output=False en la línea correspondiente:

("encoding", OneHotEncoder(handle_unknown="ignore", sparse_output=False)),
Guarda los cambios y vuelve a ejecutar tu script.