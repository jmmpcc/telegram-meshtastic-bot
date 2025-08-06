Telegram Meshtastic Bot 🤖📡
Bot de Telegram que interactúa con una red Meshtastic para monitorizar y verificar nodos, enviar mensajes de prueba y registrar resultados en CSV. Está diseñado para funcionar tanto en Windows como en Linux y utiliza la versión CLI de Meshtastic tras un enlace TCP.
Estado: Proyecto estable y en producción ✅
Lenguaje: Python ≥ 3.10
Licencia: MIT
________________________________________
Tabla de contenidos
1.	Características
2.	Capturas
3.	Requisitos
4.	Instalación
5.	Variables de entorno
6.	Uso rápido
7.	Comandos del bot
8.	Estructura del proyecto
9.	Contribuir
10.	Licencia
________________________________________
Características
Función	Descripción
/start	Menú interactivo con botones en Telegram.
/nodos	Muestra los nodos visibles, ordenados por “:last seen”.
/verificar	Traceroute + envío de mensaje a los 5 nodos más cercanos; guarda un CSV.
/traceroute	Traceroute a un nodo concreto.
/enviar	Envía texto a un nodo o canal e imprime las respuestas durante n seg.
/csv	Descarga del fichero relay_nodes.csv generado.
Escucha	Botón “🎧 Iniciar escucha” para escuchar en tiempo real un canal Meshtastic.
________________________________________
Capturas
 
Las capturas son opcionales; elimina esta sección o añade tus propias imágenes en docs/img/.
________________________________________
Requisitos
Software	Versión mínima	Notas
Python	3.10	Pruebas realizadas en 3.10 — 3.12.
Meshtastic‑CLI	2.3.0	Debe estar disponible en PATH o definir MESHTASTIC_CLI.
Git	—	Para clonar el repositorio.
Telegram Bot	—	Crea un bot con @BotFather y obtén el token.
Dependencias Python
Se instalan automáticamente desde requirements.txt (ver Instalación).
•	meshtastic ≥ 2.3
•	python-telegram-bot ≥ 21.0
•	pubsub (PyPubSub)
Windows: el bot ajusta automáticamente la política de event loop mediante asyncio.WindowsSelectorEventLoopPolicy().
________________________________________
Instalación
# 1 ‑ Clona el repositorio
$ git clone https://github.com/tu‑usuario/telegram‑meshtastic‑bot.git
$ cd telegram‑meshtastic‑bot

# 2 ‑ Crea y activa un entorno virtual (opcional pero recomendado)
$ python -m venv .venv
$ source .venv/bin/activate    # PowerShell: .venv\Scripts\Activate.ps1

# 3 ‑ Instala las dependencias
$ pip install -r requirements.txt
________________________________________
Variables de entorno
Crea un archivo `` (o define las variables en tu sistema) con las siguientes claves:
Variable	Ejemplo	Descripción
TELEGRAM_BOT_TOKEN	123456:ABC‑DEF…	Token privado de tu bot de Telegram.
TELEGRAM_ADMIN_ID	123456789	ID numérico de Telegram autorizado como admin.
MESHTASTIC_CLI	C:\Program Files\Meshtastic\meshtastic.exe	Opcional. Ruta absoluta a meshtastic.exe (Windows) si no está en PATH.
En Windows PowerShell:
setx TELEGRAM_BOT_TOKEN "123456:ABC‑DEF…"
setx TELEGRAM_ADMIN_ID  "123456789"
# Opcional
setx MESHTASTIC_CLI "C:\Program Files\Meshtastic\meshtastic.exe"
________________________________________
Uso rápido
# Ejecuta el bot
$ python telegram_bot.py
Abre Telegram, busca tu bot y envía /start. A partir de ahí utiliza el menú o los comandos directos.
Consejo: Pon el script en un servicio (systemd, NSSM, Windows Task Scheduler) para ejecución continua.
________________________________________
Comandos del bot
Comando / botón	Parámetros	Explicación
/start	—	Muestra el menú principal.
📱 Ver nodos	—	Llama a /nodos.
🧪 Verificar 5 nodos	—	Ejecuta /verificar.
📄 Descargar CSV	—	Envia relay_nodes.csv si existe.
🔁 Traceroute	ID_DEL_NODO	Después de pulsar, escribe /traceroute !abcd en el chat.
✉️ Enviar mensaje	ID canal mensaje tiempo	Ej.: /enviar canal 0 "Hola" 15 escucha 15 s tras enviar.
🎧 Iniciar escucha	—	Elige canal 0/1/2 y muestra tráfico Meshtastic en tiempo real.
⏹ Detener escucha	—	Detiene la escucha.
________________________________________
Estructura del proyecto
📁 telegram‑meshtastic‑bot/
├── telegram_bot.py                  # Lógica del bot Telegram + UI de botones
├── meshtastic_relay_checker_...py   # Utilidades Meshtastic (nodos, traceroute, CSV…)
├── requirements.txt                # Dependencias pip
├── README.md                       # Este archivo
└── docs/                           # Imágenes y documentación adicional
________________________________________
Contribuir
1.	Haz un fork del repositorio
2.	Crea una rama de características: git checkout -b feature/nueva‑feature
3.	Haz commit de tus cambios: git commit -m "Añade nueva feature"
4.	Push a la rama: git push origin feature/nueva‑feature
5.	Abre un Pull Request 🟢
Se aceptan mejoras de robustez, nuevas funciones y traducciones.
________________________________________
Licencia
Este proyecto se distribuye bajo la licencia MIT. Consulta el archivo LICENSE para más detalles.
