# LLM

Grandes modelos de lenguaje, son modelos de inteligencia artificial entrenados con cantidades masivas de texto. Su función es comprender, resumir, predecir y generar lenguaje humano de manera natural.

Conocer el top de modelos: [URL](https://llm-stats.com/leaderboards/open-llm-leaderboard)

## CONCEPTOS

* ***Open-Weight:*** un modelo Open-Weight significa que los pesos entrenados del modelo están disponibles para descargar y ejecutar. No confundir con open-source
  
  ```python
  # Por ejemplo: 
  Llama 3.1, Qwen3-Coder, DeepSeek Coder V2
  # son modelos cuyos pesos pueden descargarse y ejecutarse localmente.
  ```

* ***Parametros:*** Son los pesos que ha aprendido durante el entrenamiento. Cuantos más parámetros tiene un modelo, más capacidad suele tener para representar conocimiento y razonamiento, pero también consume más memoria y suele ser más lento.
  
  ```python
  # Ejemplos típicos:
  7B = ~7 mil millones de parámetros
  14B = ~14 mil millones
  32B = ~32 mil millones
  ```

* ***Cuantización:*** Es una técnica para reducir el tamaño de un modelo de IA sacrificando un poco de precisión a cambio de usar mucha menos memoria y ser más rápido. Recomendado(Q4_K_M), equilibrio entre cálida y tamaño. "`ollama show qwen3-coder`" Con este comando podemos ver information de tamaño/cuantización de un modelo.
  
  ```python
  | Cuantización | Calidad   | RAM necesaria      |
  | ------------ | --------- | ------------------ |
  | Q8           | Muy alta  | Más memoria        |
  | Q6           | Alta      | Menos memoria      |
  | Q5           | Muy buena | Bastante eficiente |
  | Q4           | Buena     | Muy eficiente      |
  ```

* ***Token:*** Los modelos no cuentan palabras sino tokens.
  
  ```python
  # Regla rápida
  1 token ≈ 0.75 palabras | 1000 tokens ≈ 700-800 palabras
  # Entre mas contexto mas consumo de RAM | VRAM
  ```

* ***Contexto:*** El contexto es toda la información que el modelo puede "tener presente" en una conversación o tarea antes de generar la siguiente respuesta.
  :bulb: ¿Qué entra en el contexto?:
  * Tus mensajes anteriores.
  * Las respuestas del modelo.
  * El prompt del sistema.
  * Archivos que OpenCode haya leído.
  * Código fuente que se haya enviado al modelo.
  
  ```python
  | Modelo | Contexto aproximado |
  | ------ | ------------------- |
  | 8K     | ~8.000 tokens       |
  | 32K    | ~32.000 tokens      |
  | 128K   | ~128.000 tokens     |
  | 256K   | ~256.000 tokens     |
  ```

* ***Formato:*** Es normalmente es la forma en la que el modelo se almacena en el disco.
  * GGUF → usado por Ollama y llama.cpp.
  * Safetensors → muy usado en Hugging Face.
  * PyTorch (.bin) → formato clásico de PyTorch.

## CALCULAR CONSUMO DE RAM DE UN MODELO

Para esto miramos el tamaño de la cuantización y el tamaño del contexto, sumamos la cuantización y el contexto y le restamos la mitad del contexto esto nos daría un aproximado del consumo en RAM.

## HERRAMIENTAS PARA CORRER MODELOS EN LOCAL

1. [Ollama](https://ollama.com/download):

   Herramienta que permite ejecutar modelos de inteligencia artificial, permite descargar el modelo que necesitemos.

   Documentación: [URL](https://docs.ollama.com/quickstart)

   Modelos: 

   - qwen3-coder : "Uso diario"
   - qwen2.5-coder:3b : "Modelo rapido"
   - deepseek-coder-v2:16b : "Programación pura"

   :pushpin: Abrir menú interactivo: `ollama` y se navega con las flechas.

   :pushpin: Correr un modelo `ollama run <nombre_modelo>`

1. Instalar WSL: [URL](https://learn.microsoft.com/es-es/windows/wsl/install)  
2. Instar Ubuntu: `wsl --install -d Ubuntu`
3. Abrir Ubuntu: `wsl -d Ubuntu` | o desde inicio.
4. Dentro de Ubuntu:
   `sudo apt update y sudo apt install -y curl bash`
5. Instalar OpenCode: [URL](https://opencode.ai/docs/es/windows-wsl)
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