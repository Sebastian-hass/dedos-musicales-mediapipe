# Hand Piano 🎹✋

Un piano virtual controlado por gestos de manos que utiliza visión por computadora para detectar el movimiento de los dedos y reproducir notas musicales en tiempo real.

## 🎵 Descarga de Archivos de Audio
# ⚠️ IMPORTANTE: Antes de usar la aplicación, descarga los archivos de audio necesarios desde Google Drive:
🔗 [Descargar Sonidos del Piano](https://drive.google.com/drive/folders/1zBSMzdrkD_rJwaov8iV__2zumcP99_-C?usp=sharing)
Descarga todos los archivos WAV de la carpeta y colócalos en el directorio raíz de tu proyecto.

## 📋 Descripción

Este proyecto implementa un piano virtual que se controla mediante el movimiento de los dedos detectados por una cámara web. Utiliza MediaPipe para el reconocimiento de manos y OpenCV para el procesamiento de video, permitiendo tocar diferentes notas musicales simplemente moviendo los dedos hacia abajo.

### Características principales

- **Detección de manos en tiempo real**: Reconoce hasta 2 manos simultáneamente
- **Control gestual**: Toca notas musicales al bajar los dedos índice, medio y anular
- **6 notas musicales**: Cada dedo controla una nota específica (3 dedos × 2 manos)
- **Interfaz visual**: Muestra el video en tiempo real con overlay de detección de manos
- **Audio de alta calidad**: Utiliza archivos de audio WAV para las notas musicales

## 🎵 Mapeo de Notas

| Dedo | Mano | Nota Musical |
|------|------|--------------|
| Índice | Izquierda | Fa# |
| Medio | Izquierda | La |
| Anular | Izquierda | Re |
| Índice | Derecha | Do# |
| Medio | Derecha | Sol# |
| Anular | Derecha | Si |

## 🛠️ Requisitos del Sistema

### Dependencias de Python

```
opencv-python>=4.5.0
mediapipe>=0.8.0
pygame>=2.0.0
```

### Requisitos de Hardware

- **Cámara web**: Resolución mínima 640x480
- **Micrófono/Altavoces**: Para reproducción de audio
- **Iluminación**: Ambiente bien iluminado para mejor detección

### Archivos de Audio Requeridos

El proyecto necesita los siguientes archivos de audio en formato WAV en el directorio raíz:

- `#fa.wav` - Nota Fa sostenido
- `la.wav` - Nota La
- `re.wav` - Nota Re  
- `#do.wav` - Nota Do sostenido
- `#sol.wav` - Nota Sol sostenido
- `si.wav` - Nota Si

## 📦 Instalación

1. **Clonar el repositorio**
   ```bash
   git clone [URL_DEL_REPOSITORIO]
   cd hand-piano
   ```

2. **Crear entorno virtual (recomendado)**
   ```bash
   python -m venv venv
   source venv/bin/activate  # En Windows: venv\Scripts\activate
   ```

3. **Instalar dependencias**
   ```bash
   pip install opencv-python mediapipe pygame
   ```

4. **Agregar archivos de audio**
   
   Coloca los archivos WAV de las notas musicales en el directorio raíz del proyecto con los nombres exactos especificados arriba.

## 🚀 Uso

1. **Ejecutar la aplicación**
   ```bash
   python hand_piano.py
   ```

2. **Controles**
   - Coloca tus manos frente a la cámara
   - Mueve los dedos índice, medio y anular hacia abajo para tocar notas
   - Presiona `Q` para salir de la aplicación

3. **Consejos para mejor funcionamiento**
   - Mantén las manos a una distancia de 30-60 cm de la cámara
   - Asegúrate de tener buena iluminación
   - Evita fondos muy complejos o con colores similares a la piel

## 🔧 Configuración

### Parámetros de MediaPipe

```python
min_detection_confidence=0.5    # Confianza mínima para detección inicial
min_tracking_confidence=0.5     # Confianza mínima para seguimiento
max_num_hands=2                 # Número máximo de manos a detectar
```

### Personalización de Notas

Para cambiar las notas musicales, modifica el array `sounds[]` en el código:

```python
sounds = [
    pygame.mixer.Sound("tu_nota1.wav"),  # Índice izquierdo
    pygame.mixer.Sound("tu_nota2.wav"),  # Medio izquierdo
    # ... continúa con las demás notas
]
```

## 🏗️ Arquitectura del Código

### Componentes principales

- **Inicialización de MediaPipe**: Configuración del modelo de detección de manos
- **Carga de Audio**: Inicialización de pygame mixer y carga de archivos WAV  
- **Detección de Gestos**: Función `is_finger_down()` para determinar si un dedo está hacia abajo
- **Bucle Principal**: Procesamiento de video, detección de manos y reproducción de audio
- **Control de Estado**: Seguimiento del estado de cada dedo para evitar repetición de sonidos

### Flujo de ejecución

1. Captura de frame de la cámara
2. Conversión de color BGR a RGB
3. Procesamiento con MediaPipe para detección de manos
4. Análisis de posición de dedos (índice, medio, anular)
5. Reproducción de audio basada en gestos detectados
6. Renderizado de overlay visual

## 🐛 Solución de Problemas

### Problemas Comunes

**La cámara no se inicia**
- Verifica que no esté siendo usada por otra aplicación
- Cambia el índice de la cámara: `cv2.VideoCapture(1)` en lugar de `cv2.VideoCapture(0)`

**No se detectan las manos**
- Mejora la iluminación del ambiente
- Asegúrate de que las manos estén completamente visibles
- Ajusta los parámetros de confianza de MediaPipe

**No se reproduce el audio**
- Verifica que existan todos los archivos WAV requeridos
- Comprueba que el sistema de audio esté funcionando
- Confirma que pygame esté correctamente instalado

**Detección errática**
- Mantén las manos estables frente a la cámara
- Evita movimientos muy rápidos
- Usa un fondo simple y contrastante

## 🤝 Contribuciones

Las contribuciones son bienvenidas. Para contribuir:

1. Fork el proyecto
2. Crea una rama para tu feature (`git checkout -b feature/AmazingFeature`)
3. Commit tus cambios (`git commit -m 'Add some AmazingFeature'`)
4. Push a la rama (`git push origin feature/AmazingFeature`)
5. Abre un Pull Request

## 📄 Licencia

Este proyecto fue inspirado en otros proyectos de mediapipe con intenciones puramente lectivas.

## 🙏 Reconocimientos

- **MediaPipe**: Framework de Google para procesamiento multimedia
- **OpenCV**: Biblioteca de visión por computadora
- **Pygame**: Biblioteca para desarrollo de juegos y multimedia

## 📞 Soporte

Si encuentras algún problema o tienes preguntas:

1. Revisa la sección de solución de problemas
2. Busca en los issues existentes del repositorio
3. Crea un nuevo issue con detalles específicos del problema

---

**Versión**: 1.0.0  
**Última actualización**: Julio 2025