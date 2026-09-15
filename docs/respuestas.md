¿Qué ventaja tiene registrar las dependencias del proyecto en requirements.txt en lugar de compartir la carpeta .venv? 
R: Registrar las dependencias en requirements.txt en lugar de compartir la carpeta .venv es mucho más práctico porque el archivo es ligero (unos KB vs cientos de MB), funciona en cualquier sistema operativo, y le permite a cualquier persona recrear el mismo entorno con pip install -r requirements.txt, mientras que .venv está atado a la máquina donde se creó y normalmente ni siquiera funciona si lo mueves a otra computadora. 

Pregunta (Sección 12): ¿Por qué el repositorio que tienes ahora en tu computadora no es el mismo concepto que el fork creado en GitHub?

Respuesta: El fork es una copia remota hospedada en los servidores de GitHub vinculada a tu cuenta personal, mientras que el repositorio local es el conjunto de archivos y el historial de Git descargados directamente en el almacenamiento de tu computadora física. El fork sirve como puente de sincronización en la nube para proponer cambios (Pull Request), mientras que la copia local es el entorno donde realmente se edita y ejecuta el código.

# Respuestas — Práctica Git y GitHub Naomi


## 25. Preguntas individuales

**79. ¿Cómo identificaste el comando necesario cuando la práctica no lo proporcionó?**
Identifiqué el comando necesario pensando primero en qué acción quería lograr (inicializar, revisar estado, preparar cambios, etc.) y después relacionándola con el subcomando de Git correspondiente, apoyándome en `git help` o `--help` cuando tenía dudas.

**80. ¿Qué diferencia existe entre preparar un archivo para un commit y crear el commit?**
Preparar un archivo (`git add`) lo coloca en el área de staging, marcándolo como candidato al siguiente commit, pero el cambio todavía no queda registrado en el historial. Crear el commit (`git commit`) sí registra permanentemente ese snapshot en el historial del repositorio.

**81. ¿Cómo puedes comprobar en qué rama estás trabajando?**
Con `git branch` (muestra la rama activa marcada con `*`) o con `git status`, que indica en la primera línea en qué rama estoy parado.

**82. ¿Cómo puedes determinar qué archivos fueron modificados antes de registrarlos?**
Con `git status`, que lista los archivos modificados, nuevos o eliminados antes de prepararlos para el commit.

**83. ¿Cómo puedes observar exactamente qué cambió dentro de un archivo?**
Con `git diff` (para ver cambios que aún no están en staging) o `git diff --staged` (para ver cambios ya preparados), que muestran línea por línea qué se agregó o eliminó dentro del archivo.

**84. ¿Por qué debe reconstruirse .venv después de obtener un repositorio?**
Porque la carpeta `.venv` no se sube a GitHub (está excluida en `.gitignore`), ya que contiene archivos binarios y una instalación específica de cada máquina. Por eso cada persona debe crear su propio entorno virtual localmente después de clonar u obtener el repositorio.

**85. ¿Qué relación existe entre requirements.txt y .gitignore?**
Son complementarios: `.gitignore` evita que la carpeta `.venv` (el entorno con las dependencias ya instaladas) se suba al repositorio, mientras que `requirements.txt` sí se versiona y permite que cualquier persona reconstruya ese mismo entorno ejecutando `pip install -r requirements.txt`.

**86. ¿Por qué la colaboración se realiza desde una rama y no directamente desde main?**
Porque trabajar en una rama separada evita que cambios sin terminar o sin revisar afecten directamente a `main`, que debe mantenerse siempre estable y funcional. Además, trabajar en una rama permite revisar el trabajo mediante un Pull Request antes de integrarlo.

**87. ¿Por qué una solicitud de cambios no requiere crear un Pull Request nuevo?**
Porque el Pull Request queda vinculado a la rama remota, no a un commit específico. Al hacer `git push` de nuevos commits a esa misma rama, GitHub actualiza automáticamente el contenido del PR existente en lugar de requerir uno nuevo.

**88. Después de realizar el merge en GitHub, ¿por qué todavía es necesario actualizar el repositorio local?**
Porque el merge ocurre en el repositorio remoto (GitHub), pero eso no modifica automáticamente la copia local del repositorio. Es necesario hacer `git pull` para traer esos cambios integrados a la computadora.