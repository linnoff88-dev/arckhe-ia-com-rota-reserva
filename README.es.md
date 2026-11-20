# IA com Rota Reserva

[![IA com Rota Reserva](guia/assets/hero.jpg)](https://inematds.github.io/ia-com-rota-reserva/guia/es/)

**[Português](README.md) · [English](README.en.md) · [Español](README.es.md)**

[Abre la guía y prueba la ruta alternativa](https://inematds.github.io/ia-com-rota-reserva/guia/es/)

🎬 [Video en portugués](https://www.youtube.com/watch?v=R_Mf8iMYAQk)

## Qué es

IA con Ruta de Respaldo es una guía con una demostración para quienes quieren probar herramientas de IA con límites de uso. Muestra cómo FreeLLMAPI intenta usar otro proveedor, el servicio que recibe tu solicitud y proporciona el modelo, y dónde entran Claude Desktop, Claude Code, Arena y v0. Puedes empezar por la demostración, que se ejecuta en el navegador y usa respuestas ficticias.

**Solicitud para tu asistente**

> Quiero probar una ruta de respaldo para un configurador ficticio de auriculares. El resultado debe cambiar el color y girar la vista. Usa como contexto https://inematds.github.io/ia-com-rota-reserva/guia/es/ . Sugiere una herramienta y una prueba que pueda verificar. Indica dónde se procesarían los datos y cuánto podría costar. Espera mi aprobación antes de usar servicios externos o cambiar configuraciones.

## Instalación técnica

Para probarlo sin instalar nada, [descarga el ZIP del proyecto](https://github.com/inematds/ia-com-rota-reserva/archive/refs/heads/main.zip), extrae la carpeta y haz doble clic en `guia/index.html`.

Para usar un servidor local, asegúrate de tener [Python 3](https://www.python.org/downloads/). En Windows, abre la carpeta extraída en el Explorador de archivos, escribe `powershell` en la barra de direcciones y pulsa Enter. En macOS o Linux, abre una terminal dentro de la carpeta extraída. Confirma la instalación con `python3 --version` o, en Windows, `py -3 --version`.

```sh
python3 -m http.server 18090 --bind 127.0.0.1
```

En Windows, ejecuta `py -3 -m http.server 18090 --bind 127.0.0.1` en lugar del comando anterior. El servidor permanecerá abierto en la terminal hasta que pulses Ctrl+C.

Abre `http://127.0.0.1:18090/guia/`. Selecciona **Límite de uso** en el proveedor principal y **Disponible** en el alternativo. El registro debe mostrar dos intentos y abrir un configurador en el que puedas cambiar el acabado y la rotación. Selecciona **Acceso denegado** para comprobar que la ruta se interrumpe. Si ambos servicios están temporalmente no disponibles, el configurador debe permanecer cerrado.

El configurador local usa CSS y JavaScript y ejemplifica la solicitud de producto del video. Las respuestas y los errores son simulados. La lógica del simulador es propia. Los códigos ilustrativos correspondientes serían 429 para el límite de uso, 503 para una indisponibilidad temporal y 401 o 403 para un problema de autenticación o permisos. La política de respaldo de un enrutador real varía según el proveedor, el tipo de error y la configuración.

## El proceso, de principio a fin

La referencia es [la demostración en YouTube](https://www.youtube.com/watch?v=wbchejAAe5A). La documentación de abajo se comprobó el 19 de noviembre de 2026. El guion del video de referencia contiene capítulos que difieren del archivo actual, por lo que la tabla usa los tiempos de la reproducción observada.

| En la referencia | Herramienta | Qué comprobar |
| --- | --- | --- |
| 3:43 a 7:43 | [FreeLLMAPI](https://github.com/tashfeenahmed/freellmapi) | Aplicación de escritorio o instalación local, proveedores y orden de respaldo. El puerto de la demostración era 31415. Comprueba el puerto y la clave de tu gateway. |
| 7:43 | [Claude Desktop con inferencia de terceros](https://support.claude.com/en/articles/18426225-move-from-claude-enterprise-to-claude-desktop-on-a-cloud-provider) | Disponibilidad de la configuración, URL del gateway y modelo efectivo en las rutas configuradas. |
| 10:20 | [Claude Code en la aplicación](https://support.claude.com/en/articles/18466061-move-claude-code-cli-users) | Selecciona una carpeta de prueba y autoriza solo los comandos necesarios. En el configurador de auriculares, prueba el color, el material y la rotación después de la compilación. |
| 11:39 | [Claude Code en la terminal](https://code.claude.com/docs/en/llm-gateway) | Dirige la sesión al gateway, selecciona una cadena con opciones habilitadas y envía primero una solicitud breve. |
| 13:32 | FreeLLMAPI Playground | El prototipo del video recibía un PDF. En una prueba real, abre el archivo descargado y comprueba que el contenido y el formato sean correctos. |
| 15:49 | [Arena Model API](https://platform.arena.ai/docs/api) | La documentación actual indica `https://api.arena.ai` para clientes de Anthropic. El acceso directo a un modelo requiere fondos pagados o crédito promocional válido. Consulta la cuenta antes de ejecutarlo. |
| 17:23 | [v0](https://v0.app/pricing) | El plan Free indica siete mensajes al día en la consulta de esta fecha. El anuncio de crédito de la referencia y la elección de Fable 5.2 dependen de la oferta y de la cuenta. |

En la instalación mostrada, FreeLLMAPI usa Google AI Studio, Kilo Gateway, OpenRouter, NVIDIA, Z.ai y Cloudflare Workers AI. El [README oficial](https://github.com/tashfeenahmed/freellmapi) mantiene la lista actualizada. Después de descargar una versión compatible desde la página de [releases](https://github.com/tashfeenahmed/freellmapi/releases), habilita solo los proveedores cuyos términos y posibles costes hayas comprobado. Configura al menos dos en la cadena de respaldo y haz la primera prueba con datos ficticios.

### Prueba con servicios reales

1. Instala [Claude Code](https://code.claude.com/docs/en/setup) y comprueba `claude --version`. Descarga [FreeLLMAPI](https://github.com/tashfeenahmed/freellmapi/releases) para tu plataforma. En instalaciones de servidor, sigue la [guía oficial](https://github.com/tashfeenahmed/freellmapi#quick-start).
2. Abre FreeLLMAPI. En **Keys**, habilita dos proveedores que puedas usar y registra las claves cuando se te soliciten. Comprueba sus límites antes de continuar. En **Models → Fallback chains**, crea `free-claude-code` si aún no existe, habilita los dos modelos en el orden que prefieras y guarda. Haz una prueba en **Playground** con una pregunta breve y comprueba qué opción respondió.
3. En el panel de FreeLLMAPI, copia la URL base de Anthropic y la clave unificada. La [documentación de FreeLLMAPI para clientes](https://github.com/tashfeenahmed/freellmapi/blob/main/docs/en/clients/01-agent-clients.md#claude-desktop-third-party-gateway) indica `http://127.0.0.1:31415` en la aplicación y `http://localhost:3001` en la instalación de servidor. Usa el origen sin `/v1`.
4. En Claude Desktop, si está disponible la configuración de terceros, abre **Setup → Gateway**. En las versiones que incluyen el menú de la referencia, usa **Help → Troubleshooting → Developer Mode** y luego **Developer → Configure third-party inference**. Si el menú no aparece, consulta los requisitos de tu versión y organización. Usa esa URL y la clave unificada con autenticación `x-api-key`, haz una prueba y guarda. Comprueba la asignación de modelos en FreeLLMAPI. La pestaña **Code** hereda la configuración de terceros de la aplicación.
5. En Claude Code instalado por separado, abre una nueva sesión de Bash en una carpeta de prueba y pega el bloque siguiente con la URL de tu instalación. Al ejecutarlo, pega la clave unificada en el prompt oculto. La subsesión mantiene las variables fuera de tu terminal habitual.

Si FreeLLMAPI está en Windows, ejecuta Claude Code en el mismo Windows y usa la opción de [PowerShell del manual de FreeLLMAPI](https://github.com/tashfeenahmed/freellmapi/blob/main/docs/en/clients/01-agent-clients.md#coding-agents). El bloque Bash de abajo sirve para macOS y Linux con el router en el mismo entorno.

```bash
(
  export ANTHROPIC_BASE_URL=http://127.0.0.1:31415
  read -rsp 'Clave unificada de FreeLLMAPI: ' ANTHROPIC_AUTH_TOKEN
  printf '\n'
  if [ -z "$ANTHROPIC_AUTH_TOKEN" ]; then
    echo 'Introduce una clave para continuar.' >&2
    exit 1
  fi
  export ANTHROPIC_AUTH_TOKEN
  export ANTHROPIC_MODEL=auto:free-claude-code
  claude
)
```

Pide una respuesta de una frase y comprueba en el registro del enrutador quién respondió. Si el mensaje indica que la cadena está vacía, comprueba los modelos habilitados. Si faltan permisos, revisa la clave antes de volver a intentarlo. Anthropic documenta la conexión mediante gateway, pero [no ofrece soporte para Claude Code con modelos que no sean Claude](https://code.claude.com/docs/en/llm-gateway). La integración con proveedores externos requiere tus credenciales y no se ejecutó en la demostración de este proyecto. Usa datos ficticios hasta verificar las condiciones, la retención, los límites y los permisos.

#### Ejemplos de claves

Dos opciones de referencia para encontrar claves API

- **Google AI Studio**. Ve a [API keys](https://aistudio.google.com/apikey), crea una clave y selecciona Google AI Studio en **Keys → Add key** en FreeLLMAPI. Comprueba antes que la facturación esté habilitada para tu proyecto de Google.
- **NVIDIA**. Elige un modelo en el [catálogo de NVIDIA](https://build.nvidia.com/explore/discover), inicia sesión en tu cuenta y usa **Get API Key** según la [guía oficial](https://docs.api.nvidia.com/nim/re/docs/api-quickstart). Selecciona NVIDIA en **Keys → Add key**.

Estas claves permiten que FreeLLMAPI se comunique con cada servicio. La clave unificada es otra: funciona como la contraseña de tu aplicación para comunicarse con FreeLLMAPI. El gateway es la dirección del enrutador que reenvía las solicitudes. Usa la URL base que aparece en el panel, sin añadir `/v1`.
