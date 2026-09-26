# Manual de Uso - Audio Transcriber y Script Generator

## Índice
1. [Estructura de Directorios](#estructura-de-directorios)
2. [Preparación del Entorno](#preparación-del-entorno)
3. [Configuración Inicial](#configuración-inicial)
4. [Uso del Servicio](#uso-del-servicio)
5. [Opciones de Comando](#opciones-de-comando)
6. [Ejemplos de Uso](#ejemplos-de-uso)
7. [Archivos de Salida](#archivos-de-salida)

## Estructura de Directorios

El servicio utiliza la siguiente estructura de directorios:

```
.
├── voice_notes/         # Directorio para archivos de audio de entrada
├── segments_audio/      # Directorio para segmentos de audio (generado automáticamente)
├── transcriptions/      # Directorio para transcripciones de texto
├── ai_text_notes/      # Directorio para scripts generados
└── keypoints/          # Directorio para puntos clave extraídos
```

### Directorios de Entrada
- **voice_notes/**: Coloca aquí tus archivos de audio en formato .m4a o .mp3
  - Ejemplo: `voice_notes/mi_reunion.m4a`

### Directorios de Salida
- **transcriptions/**: Contiene las transcripciones de texto de los audios
- **ai_text_notes/**: Almacena los scripts cinematográficos generados
- **keypoints/**: Guarda los resúmenes de puntos clave
- **segments_audio/**: Contiene los segmentos de audio procesados (se crea automáticamente)

## Preparación del Entorno

1. **Instalación de Dependencias**
   ```bash
   pip install openai pydub python-dotenv tqdm
   ```

2. **Configuración de Variables de Entorno**
   Crea un archivo `.env` en la raíz del proyecto con:
   ```
   OPENAI_ORGANIZATION=tu_organización_openai
   OPENAI_PROYJECT=tu_proyecto_openai
   OPENAI_API_KEY=tu_api_key_openai
   ```

## Uso del Servicio

### Modo Interactivo
Para usar el servicio de forma interactiva:
```bash
python main.py
```
El programa te guiará para:
1. Seleccionar el archivo de audio
2. Elegir las acciones a realizar
3. Configurar opciones adicionales

### Modo por Comandos
Puedes usar el servicio con comandos específicos:
```bash
python main.py --audio "nombre_archivo" [opciones]
```

## Opciones de Comando

| Opción        | Descripción                                                                 |
|---------------|-----------------------------------------------------------------------------|
| `--transcript` | Realiza solo la transcripción del audio                                    |
| `--script`     | Genera un script basado en la transcripción                                |
| `--keypoints`  | Extrae los puntos clave del audio                                         |
| `--tone`       | Define el tono del script (ej: "Inspirador", "Motivacional")              |
| `--audio`      | Nombre del archivo de audio (sin extensión)                               |
| `--duracion`   | Duración aproximada del script en minutos                                 |

## Ejemplos de Uso

### 1. Transcripción Simple
```bash
python main.py --audio "mi_reunion" --transcript
```

### 2. Generar Script Cinematográfico
```bash
python main.py --audio "mi_reunion" --script --tone "Inspirador" --duracion 5
```

### 3. Extraer Puntos Clave
```bash
python main.py --audio "mi_reunion" --keypoints
```

### 4. Proceso Completo
```bash
python main.py --audio "mi_reunion" --transcript --script --keypoints --tone "Motivacional" --duracion 10
```

## Archivos de Salida

### Transcripciones
- **Ubicación**: `transcriptions/`
- **Formato**: Archivos de texto (.txt)
- **Ejemplo**: `transcriptions/mi_reunion.txt`

### Scripts Generados
- **Ubicación**: `ai_text_notes/`
- **Formato**: Archivos de texto (.txt)
- **Ejemplo**: `ai_text_notes/mi_reunion_script.txt`

### Puntos Clave
- **Ubicación**: `keypoints/`
- **Formato**: Archivos de texto (.txt)
- **Ejemplo**: `keypoints/mi_reunion_keypoints.txt`

### Segmentos de Audio
- **Ubicación**: `segments_audio/`
- **Formato**: Archivos de audio (.mp3)
- **Nota**: Estos archivos se generan automáticamente durante el procesamiento

## Notas Importantes

1. Los directorios se crean automáticamente si no existen
2. Si un archivo de salida ya existe, el programa omitirá su creación para ahorrar recursos
3. Para forzar la regeneración de un archivo, usa la opción específica (--transcript, --script)
4. El programa optimiza el procesamiento para evitar trabajo redundante 