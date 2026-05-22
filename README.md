# Facial Emotion Detection — Dataset

El dataset original (`Facial_emotion_images.zip`) supera el límite de 25 MB de GitHub,
por lo que se ha dividido en cuatro archivos, uno por clase de emoción:

| Archivo | Clase | Tamaño |
|---|---|---|
| `emotions_happy.zip` | Happy | ~10 MB |
| `emotions_sad.zip` | Sad | ~8.5 MB |
| `emotions_neutral.zip` | Neutral | ~8.7 MB |
| `emotions_surprise.zip` | Surprise | ~6.9 MB |

Cada zip contiene las carpetas `train/`, `validation/` y `test/` de su clase correspondiente.

---

## Opción A — Reconstruir el zip original

Si quieres trabajar con el notebook sin modificar ninguna celda, descarga los cuatro zips,
extráelos todos en la misma carpeta y tendrás la estructura original:

```
Facial_emotion_images/
├── train/
│   ├── happy/
│   ├── sad/
│   ├── neutral/
│   └── surprise/
├── validation/
│   └── ...
└── test/
    └── ...
```

En Google Colab, después de subir los cuatro zips a tu Google Drive, ejecuta esto
**en lugar de** la celda de descompresión original:

```python
import zipfile

zips = [
    '/content/drive/MyDrive/emotions_happy.zip',
    '/content/drive/MyDrive/emotions_sad.zip',
    '/content/drive/MyDrive/emotions_neutral.zip',
    '/content/drive/MyDrive/emotions_surprise.zip',
]

for path in zips:
    with zipfile.ZipFile(path, 'r') as zip_ref:
        zip_ref.extractall('Facial_emotion_images/')
```

El resto del notebook no necesita ningún cambio.

---

## Opción B — Adaptar el notebook (sin reconstruir el zip)

Sustituye la celda de descompresión original por el mismo bloque de la Opción A.
El `folder_path` y todos los data loaders posteriores funcionan igual porque
la estructura de carpetas resultante es idéntica.
