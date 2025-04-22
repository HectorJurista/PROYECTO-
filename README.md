# PROYECTO-
PAPELERA PORTAL A LA INTERNET MUERTA
🎯 Objetivo:
Cuando vacíes o abras la papelera, se lanzará automáticamente un programa que muestra contenido de la “Internet Muerta”: páginas desaparecidas, textos abandonados, arte digital oculto, etc.

🧠 Concepto técnico
Usaremos:

Script en Python para monitorear la papelera.

Acceso a sitios como Wayback Machine para explorar archivos muertos.

Interfaz visual simple que se abre cuando interactúas con la papelera.

🧰 Herramientas necesarias:
Python 3.10 o superior

Librerías:

bash
Copiar
Editar
pip install watchdog requests beautifulsoup4
Acceso a Internet

Sistema operativo Windows o Linux (se puede adaptar a Mac)

🧾 Paso 1: Script que detecta vaciado o apertura de la papelera
python
Copiar
Editar
import os
import time
from watchdog.observers import Observer
from watchdog.events import FileSystemEventHandler
import webbrowser

# Ruta de la papelera (en Windows)
RECYCLE_BIN_PATH = os.path.expandvars(r"$Recycle.Bin")

class RecycleBinHandler(FileSystemEventHandler):
    def on_modified(self, event):
        print("⚠️ Papelera de reciclaje modificada...")
        # Abre una URL archivada como "puerta"
        open_dead_internet_portal()

def open_dead_internet_portal():
    # Página muerta en archive.org como demo
    archived_url = "https://web.archive.org/web/20050212072630/http://geocities.com/"
    webbrowser.open(archived_url)

if __name__ == "__main__":
    print("👁️ Vigilando la papelera...")

    event_handler = RecycleBinHandler()
    observer = Observer()
    observer.schedule(event_handler, path=RECYCLE_BIN_PATH, recursive=True)
    observer.start()

    try:
        while True:
            time.sleep(5)
    except KeyboardInterrupt:
        observer.stop()
    observer.join()
🖼️ Paso 2: Mejora visual (opcional)
Podrías reemplazar webbrowser.open(...) con una app visual en Python (con tkinter o PyQt) que muestre:

Archivos viejos indexados en Wayback Machine

Fragmentos de foros de los 2000s

Fragmentos de arte glitch o ASCII

Textos tipo creepypasta o cyberpunk

🔮 Idea filosófica
Esto convierte la papelera (el olvido digital) en un portal al pasado de Internet, a lo abandonado, lo olvidado, lo no indexado. La “Internet Muerta” es un cementerio digital, y tú estás construyendo un ritual de acceso.

