# LLM

Grandes modelos de lenguaje, son modelos de inteligencia artificial entrenados con cantidades masivas de texto. Su función es comprender, resumir, predecir y generar lenguaje humano de manera natural.

## INSTALAR LOCAL

1. [Ollama](https://ollama.com/download):

   Herramienta que permite ejecutar modelos de inteligencia artificial, permite descargar el modelo que necesitemos.

   Documentación: [URL](https://docs.ollama.com/quickstart)

   Modelos: 

   - qwen3-coder : "Uso diario"
   - qwen2.5-coder:3b : "Modelo rapido"
   - deepseek-coder-v2:16b : "Programación pura"

   :pushpin: Abrir menú interactivo: `ollama` y se navega con las flechas.

   :pushpin: Correr un modelo `ollama run <nombre_modelo>`

2. Instalar WSL: [URL](https://learn.microsoft.com/es-es/windows/wsl/install)  
3. Instar Ubuntu: `wsl --install -d Ubuntu`
4. Abrir Ubuntu: `wsl -d Ubuntu` | o desde inicio.
5. Dentro de Ubuntu:
   `sudo apt update y sudo apt install -y curl bash`
6. Instalar OpenCode: [URL](https://opencode.ai/docs/es/windows-wsl)
   1.  Abrir WSL + ubutnu y ejecutar `curl -fsSL https://opencode.ai/install | bash` para finalizar `source ~/.bashrc`
   2. abrir el app `opencode`

```python
'''
Si instalamos OpenCode en WSL Ubuntu y Ollama lo tenemos en Windows el comando directo ollama lauch opencode no funcionara.
	Esto es porque ollama se encuentra aislado.

Solucion:
Configuracion en Windows:
1. Cerrar Ollama en windows.
2. Editar las variables de entorno.
	rundll32.exe sysdm.cpl,EditEnvironmentVariables
	En variables de usuario agregar:
		Nombre de la variable: OLLAMA_HOST
		Valor de la variable: 0.0000 (o 0.0.0.0:11434)
		
Configuracion de OpenCode en WSL
Como no podemos utilizar un putnte automatico ollama launch, escribiremos esta configuracion nosotros mismos en el archivo JSON de OpenCode en WSL para que este apunte a windows.
1. nano ~/.config/opencode/opencode.json
2. Pegar el siguiente contenido (asegúrate de cambiar `gemma4:26b` o el nombre del modelo por el que tú tengas descargado en tu Ollama de Windows):

{
  "$schema": "https://opencode.ai/config.json",
  "provider": {
    "ollama": {
      "npm": "@ai-sdk/openai-compatible",
      "options": {
        "baseURL": "http://localhost:11434/v1"
      },
      "models": {
        "gemma4:26b": {
          "name": "Ollama - Gemma 4"
        }
      }
    }
  }
}

Guardar Ctrl + 0 > Enter > Salir con Ctrl + X

Nota:
WSL mapea automaticamente el localhost de ubuntu al de nuestro windows, por esto utilizar "http://localhost:11434/v1" dentro de WSL funciona perfectamente.
'''
```

### OPENCODE

Guia para instalar OpenCode: [URL](https://opencode.ai/docs/es).
:key: Configurar OpenCode para que detecte modelos locales de Ollama:

1. Abrir ubicacion del archivo JSON de Ollama.
`~/.config/opencode/opencode.json`
2. Abrir con el json con editor.
`[vim, nano]`
3. Pegar la siguiente estructura:
```json
{
  "$schema": "https://opencode.ai/config.json",

  "provider": {
    "ollama": {
      "npm": "@ai-sdk/openai-compatible",
      "name": "Ollama",

      "options": {
        "baseURL": "http://127.0.0.1:11434/v1"
      },

      "models": {
        "qwen3-coder:latest": {
          "name": "Qwen3 Coder",
          "tools": true
        },

        "deepseek-coder-v2:16b": {
          "name": "DeepSeek Coder V2 16B",
          "tools": true
        }
      }
    }
  },

  "model": "ollama/qwen3-coder:latest",
  "small_model": "ollama/deepseek-coder-v2:16b"
}
```