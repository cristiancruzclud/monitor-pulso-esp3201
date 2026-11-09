# ❤️ Monitor de Pulso Cardíaco con ESP32

**Sensor de pulso analógico · Pantalla TFT ST7789 · Visualización de BPM**
Proyecto académico – UNISANGIL, sede Yopal

![ESP32](https://img.shields.io/badge/ESP32-Arduino-blue) ![Pantalla](https://img.shields.io/badge/Pantalla-ST7789%20240x280-green) ![Tipo](https://img.shields.io/badge/Tipo-Educativo-orange)

## 🔗 Accesos rápidos

| Recurso | Enlace |
|---------|--------|
| 💻 Código fuente | [`src/Monitor_Pulso_ESP32_ST7789_v2.ino`](src/Monitor_Pulso_ESP32_ST7789_v2.ino) |
| 🎥 Video 1 | [YouTube Shorts](https://youtube.com/shorts/sWyu3B2UVCs) |
| 🎥 Video 2 | [YouTube Shorts](https://youtube.com/shorts/KdcVzdf5wLg) |
| 📄 Informe IEEE | [`docs/Informe_Monitor_de_Pulso_IEEE.pdf`](docs/Informe_Monitor_de_Pulso_IEEE.pdf) |

## 📌 Descripción

Este proyecto implementa un monitor educativo de pulso cardíaco con un ESP32, un sensor óptico de pulso analógico y una pantalla TFT ST7789 de 240 × 280 píxeles. El sistema adquiere la señal del sensor, la procesa para detectar los latidos, estima la frecuencia cardíaca en pulsaciones por minuto (BPM) y la presenta junto con la onda de pulso.

> **Aviso importante:** este es un prototipo académico, **no un dispositivo médico**. No debe utilizarse para diagnóstico ni para decisiones clínicas. Usa un sensor analógico de un solo canal y **no mide SpO₂**.

## ✨ Características

- Lectura analógica con el ADC de 12 bits del ESP32.
- Muestreo a 100 Hz.
- Suavizado de la señal y eliminación de la línea base.
- Detección de latidos con umbral adaptativo.
- BPM calculado con la mediana de los intervalos, validando su regularidad.
- Visualización de BPM, estado y onda de pulso en la pantalla TFT.
- Corazón animado en dos tiempos (lub-dub) y aviso sonoro con buzzer en cada latido.
- Salida al Monitor Serie o al Serial Plotter de Arduino IDE.

## 🧰 Componentes

| Componente | Función |
|------------|---------|
| ESP32 (clásico, DevKit) | Adquisición y procesamiento |
| Sensor óptico de pulso analógico de 3 pines | Captura de la señal de pulso |
| Pantalla TFT ST7789 240×280 | Interfaz gráfica |
| Buzzer activo | Aviso sonoro por latido |
| Placa de expansión y cables Dupont | Conexiones |
| Cable USB | Alimentación y programación |

## 🔌 Conexiones

**Pantalla TFT ST7789**

| Pin de la pantalla | ESP32 |
|--------------------|-------|
| SCL / SCK | GPIO 18 |
| SDA / MOSI | GPIO 23 |
| RES | GPIO 4 |
| DC | GPIO 2 |
| CS | GPIO 5 |
| VCC | 3,3 V |
| BLK | 3,3 V |
| GND | GND |

**Sensor de pulso analógico**

| Pin del sensor | ESP32 |
|----------------|-------|
| VCC / + | 3,3 V |
| GND / − | GND |
| S / señal | GPIO 34 |

**Buzzer activo**

| Pin del buzzer | ESP32 |
|----------------|-------|
| Positivo (+) | GPIO 25 |
| Negativo (−) | GND |

> La pantalla usa SPI; sus etiquetas SDA y SCL corresponden a MOSI y SCK. El sensor se lee por el ADC (GPIO34) y no usa I²C. Comprueba el pinout impreso en tus módulos antes de energizar el circuito.

## 💻 Software y bibliotecas

1. Instala [Arduino IDE](https://www.arduino.cc/en/software).
2. Selecciona una placa ESP32, por ejemplo **ESP32 Dev Module**.
3. Desde el Gestor de bibliotecas instala:
   - **Adafruit GFX Library**
   - **Adafruit ST7735 and ST7789 Library**
   - **Adafruit BusIO** (si el gestor la pide como dependencia)
4. Abre el archivo `.ino` de la carpeta `src`.
5. Elige el puerto COM y carga el programa.

Comunicación serial a **115200 baudios**.

## 🚀 Código fuente

El sketch [`src/Monitor_Pulso_ESP32_ST7789_v2.ino`](src/Monitor_Pulso_ESP32_ST7789_v2.ino) corresponde a la versión 2 (buzzer activo y corazón animado).

- `MODO_PLOTTER=true`: salida para el Serial Plotter (series Pulso, BPM, Latido, Techo).
- `MODO_PLOTTER=false`: texto en el Monitor Serie con el valor crudo.
- Sin señal válida, el BPM aparece como `--` en pantalla o `0` en la salida serial.

## 📈 Uso del monitor

1. Alimenta el ESP32 por USB.
2. Espera a que aparezca la interfaz en la pantalla.
3. Apoya suavemente la yema del dedo sobre el sensor, sin presionar demasiado.
4. Mantén el dedo quieto mientras se estabiliza la lectura.
5. Observa el BPM y la onda en la pantalla.
6. Para ver los datos, abre el Serial Plotter a 115200 baudios.

## 🎥 Videos de demostración

- ▶ [Demostración 1](https://youtube.com/shorts/sWyu3B2UVCs)
- ▶ [Demostración 2](https://youtube.com/shorts/KdcVzdf5wLg)

(También en [`videos/ENLACES_VIDEOS.md`](videos/ENLACES_VIDEOS.md)).

## 📄 Informe académico

Informe en formato IEEE disponible en la carpeta [`docs/`](docs/).

## 📁 Estructura del repositorio

```
Monitor-de-Pulso-ESP32/
├── README.md
├── src/
│   └── Monitor_Pulso_ESP32_ST7789_v2.ino
├── docs/
│   ├── README.md
│   └── Informe_Monitor_de_Pulso_IEEE.pdf
└── videos/
    └── ENLACES_VIDEOS.md
```

## 👨‍💻 Autores

- Cristian Enrique Cruz Fernández
- Samuel Felipe Díaz Galindo
- Santiago Reina Socha

Fundación Universitaria de San Gil – UNISANGIL, sede Yopal, Yopal, Casanare, Colombia.
