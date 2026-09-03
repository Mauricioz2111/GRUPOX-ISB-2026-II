# SEGUNDO LABORATORIO
## LAB 01: Lectura, Exploración y Exportación de Señales ECG a Audio

Este laboratorio aborda la descarga, exploración gráfica, análisis estadístico y exportación a formato `.wav` de un registro electrocardiográfico (ECG) desde la plataforma **PhysioNet**.

**IDENTIFICACIÓN DEL REGISTRO**
* **Identificador único:** Acceder a una base de datos fisiológica de PhysioNet usando la combinación de `DATABASE + RECORD` (`mitdb` + `100`). Cabe resaltar que en función a la base de datos, el número de registro puede significar algo distinto.

**PARÁMETROS CONFIGURABLES**
| Parámetro | Descripción | Ejemplo |
| :--- | :--- | :--- |
| `DATABASE` | Base de datos de PhysioNet | `"mitdb"` |
| `RECORD` | Identificador del registro | `"100"` |
| `CHANNEL` | Canal que se desea analizar | `0` |
| `DURATION` | Duración del segmento en segundos | `10` |
| `OUTPUT_WAV` | Nombre del archivo WAV | `ecg_100.wav` |

**EXTRAER REGISTROS**
A lo largo del laboratorio utilizaremos distintas librerías como:
* **WFDB**: Acceso a registros de PhysioNet
* **NumPy**: Procesamiento numérico
* **Pandas**: Organización de datos
* **Matplotlib**: Visualización
* **SciPy**: Exportación de la señal a Wav

En un principio, se carga el registro con `wfdb.rdrecord()` e identificamos la frecuencia de muestreo, número de muestras, número de canales, nombre de los canales y las unidades de las señales. 

Posteriormente, se extrae las muestras de la señal y se guarda en una variable: `signal = record.p_signal[:, CHANNEL]`. Después, se procede a construir un eje temporal $t[n] = \frac{n}{f_s}$, esta relación es fundamental para interpretar correctamente una señal biomédica.

**GRAFICAR LAS SEÑALES**
En este primer laboratorio se llega a graficar tres señales: ECG completo, segmento de 10s ampliado, histograma de amplitudes y la representación discreta de las primeras 100 muestras. 

**ESTADÍSTICA BÁSICA DE LA SEÑAL**
* **MEDIA**: `np.mean(signal_segment)`
* **DESVIACIÓN ESTÁNDAR**: `np.std(signal_segment)`
* **MÍNIMO**: `np.min(signal_segment)`
* **MÁXIMO**: `np.max(signal_segment)`
* **RANGO**: `MÁXIMO - MÍNIMO`

**CONVERSIÓN DEL ECG A FORMATO .WAV**
El formato WAV es común en aplicaciones de audio. Sin embargo, nuestra señal es un ECG, por lo que para almacenarlo seguimos el siguiente flujo:
```text
ECG ORIGINAL
 ↓
Eliminar componente media
 ↓
Normalizar amplitud
 ↓
Convertir a `int16`
 ↓
Guardar WAV
```
**¿POR QUÉ NORMALIZAR?**: Los valores de ECG están expresados en unidades fisiológicas, mientras que el WAV suele utilizar representaciones enteras, como `int16`.

## LAB 02: Análisis Multidominio (Temporal, FFT y STFT)

Este laboratorio evalúa tres registros de la base de datos `nsrdb` (`16265`, `16272` y `16420`), comparando su comportamiento en el dominio del tiempo, la frecuencia y tiempo-frecuencia.

**RECORDANDO TEORÍA**
* **DOMINIO TEMPORAL**: Permite estudiar cómo cambia la amplitud de la señal con el tiempo: $x(t)$ 
* **DOMINIO FRECUENCIAL**: La FFT permite analizar qué componentes de frecuencia están presentes en una señal: $X[f] = \mathcal{F}\{x(t)\}$ 
* **DOMINIO TIEMPO-FRECUENCIA**: La STFT permite observar cómo evoluciona el contenido frecuencial a lo largo del tiempo

**PARÁMETROS DEL EJERCICIO**
| Parámetro | Valor |
| :--- | :--- | 
| **BASE DE DATOS** | `nsrdb` | 
| **REGISTRO 1** | `16265` | 
| **REGISTRO 2** | `16272` | 
| **REGISTRO 3** | `16420` | 
| **MUESTRAS** | `3600` por registro | 
| **CANAL ANALIZADO** | `0` | 

**EXTRAER REGISTROS**
A lo largo de este segundo laboratorio utilizaremos las siguientes librerías:
* **WFDB**: Acceso a registros de PhysioNet
* **NumPy**: Procesamiento numérico
* **SciPy**: Cálculo de la STFT
* **Matplotlib**: Visualización

La función principal utilizada será: `wfdb.rdrecord()`
A continuación se muestra el código utilizado para cargar y extraer los 3 registros que se usarán a lo largo del laboratorio :

```bash

# CARGAR LOS TRES REGISTROS

records_data = {}

for record_name in RECORDS:
    record = wfdb.rdrecord(
        record_name,
        pn_dir=DATABASE,
        sampfrom=SAMPFROM,
        sampto=SAMPFROM + SAMPLING_POINTS
    )

    records_data[record_name] = record

    print(f"Registro {record_name} cargado correctamente.")


# CARGAR ANOTACIONES

annotations = {}

for record_name in RECORDS:
    try:
        annotation = wfdb.rdann(
            record_name,
            "atr",
            pn_dir=DATABASE,
            sampfrom=SAMPFROM,
            sampto=SAMPFROM + SAMPLING_POINTS
        )
        annotations[record_name] = annotation
        print(f"Anotaciones del registro {record_name}: {len(annotation.sample)}")
    except Exception as e:
        annotations[record_name] = None
        print(f"No fue posible cargar anotaciones para {record_name}: {e}")


# EXTRAER SEÑALES Y EJES TEMPORALES

signals = {}
times = {}
sampling_rates = {}

for record_name, record in records_data.items():
    x = record.p_signal[:, CHANNEL]
    fs = record.fs

    signals[record_name] = x
    sampling_rates[record_name] = fs
    times[record_name] = np.arange(len(x)) / fs

    print(
        f"{record_name}: "
        f"{len(x)} muestras, "
        f"fs = {fs} Hz, "
        f"canal = {record.sig_name[CHANNEL]}"
    )

```
Las muestras se encuentran en `record.p_signal`, la estructura tiene la forma (muestras, canales). Por ello, para seleccionar el canal indicado guardamos `record.p_signal[:, CHANNEL]` en una variable y contruimos el eje temporal.


**CALCULO DE A FFT Y LA STFT**
* **TRANSFORMADA RÁPIDA DE FOURIER (FFT)**: Permite transformar una señal del dominio temporal a dominio frecuencial. En el presente laboratorio se calcula la FFT de cada registro en dos versiones:
    * **Con la componente DC**
    * **Después de eliminar la MEDIA**
Se identifica la frecuencia dominante de cada registro (ignorando 0Hz para no voler a capturar la componente DC). La frecuencia dominante encontrada mediante FFT no debe interpretarse automáticamente como una frecuencia fisiológica específica. Es necesario considerar el tipo de señal, el procesamiento aplicado y el contexto del registro.

* **TRANSFORMADA DE FOURIER DE TIEMPO CORTO (STFT)**: Proporciona información sobre el contenido frecuencial global de una señal; sin embargo, si queremos saber cuándo aparecen determinadas componentes de frecuencia necesitamos una representación tiempo-frecuencia.
La STFT divide la señal en "ventanas" y calcula una FFT para cada una. Una ventana pequeña significa una mejor resolución temporal; por el contrario, una ventana grande, una menor resolución.
Además se grafica un espectrograma usando una ventana grande (`nperseg=256`) para los registros `16265/16420` y una pequeña (`nperseg=32`) para `16272` (para conservar mejor eventos localizados en el tiempo).


## LAB 03: Diseño y Aplicación de Filtros Digitales (FIR e IIR) en Señales Biomédicas

En este laboratorio se aborda la teoría, caracterización y procesamiento digital de señales electrocardiográficas (ECG) mediante transformadas de Fourier (FFT), Transformada Z y el diseño comparativo de filtros FIR e IIR.

**Fundamentos de Procesamiento Digital de Señales**
* **Señal discreta:** Definida en el índice de muestra $n$ con un periodo $T_s = 1/f_s$. La frecuencia de muestreo determina el límite de Nyquist ($f_{\text{max}} = f_s/2$).
* **Transformada de Fourier (FFT):** Algoritmo eficiente para calcular la DFT que descompone la señal temporal en componentes espectrales.
* **Transformada Z y relación frecuencial:** Representa sistemas discretos mediante ceros y polos en la función de transferencia $H(z)$. Evaluar $H(z)$ sobre el círculo unitario ($z = e^{j\omega}$) proporciona la respuesta en frecuencia de Fourier.
* **Filtros FIR:** No poseen realimentación, son siempre estables y permiten obtener fase lineal fácilmente, aunque requieren un orden más elevado.
* **Filtros IIR:** Utilizan realimentación (polos), logrando atenuaciones similares con órdenes menores, pero requieren análisis de estabilidad y pueden distorsionar la fase.

**Entorno Experimental y Caracterización de la Señal**
* **Parámetros de entrada:** Registro ECG sintético (`neurokit2`) de 3600 muestras, 250 Hz y frecuencia cardíaca de 70 bpm (14.40 s de duración).
* **Inspección de archivos:** Se valida el formato de origen (`wavfile.read`) verificando canales, tipo de dato y duración antes de cualquier filtrado.
* **Espectro fisiológico:** La FFT revela que la mayor parte de la energía clínica del ECG (ondas P, T y complejo QRS) se concentra en la banda de 0.5 Hz a 40 Hz.

**Diseño de Filtros y Remoción de Ruido**
* **Estrategia Pasa-Bajos (40 Hz):** Implementación de filtro FIR (101 coeficientes) e IIR Butterworth (4.º orden en secciones de segundo orden SOS) para eliminar ruido de alta frecuencia manteniendo la morfología QRS.
* **Eliminación de interferencia de 35 Hz:** Al detectar un pico de ruido agudo mediante la FFT, se aplicó un filtro pasa-bajos IIR Butterworth con frecuencia de corte a 25 Hz empleando `sosfiltfilt` (filtrado bidireccional de fase cero).

**Validación y Análisis de Errores de Diseño**
* **Métricas de desempeño:** La calidad de la señal se valida cuantificando la reducción del MSE/RMSE y el incremento en el SNR tras el filtrado.
* **Frecuencia de corte excesivamente baja (5 Hz):** Elimina energía fundamental del complejo QRS, provocando su aplanamiento y ensanchamiento, lo que destruye la validez diagnóstica.
* **Desplazamiento de fase (`sosfilt` unidireccional):** Produce retardo de grupo no lineal, desplazando los picos R en el tiempo y alterando la medición precisa de los intervalos cardiacos (PR, QT).
