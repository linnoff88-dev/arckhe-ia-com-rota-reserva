# IA com Rota Reserva

[![IA com Rota Reserva](guia/assets/hero.jpg)](https://inematds.github.io/ia-com-rota-reserva/guia/en/)

**[Português](README.md) · [English](README.en.md) · [Español](README.es.md)**

[Open the guide and test the backup route](https://inematds.github.io/ia-com-rota-reserva/guia/en/)

🎬 [Video in Portuguese](https://www.youtube.com/watch?v=R_Mf8iMYAQk)

## What it is

IA com Rota Reserva is a guide with a demonstration for people who want to try AI tools with usage limits. It shows how FreeLLMAPI tries another provider—the service that receives your request and supplies the model—and where Claude Desktop, Claude Code, Arena, and v0 fit in. You can start with the demonstration, which runs in your browser and uses fictional responses.

**Prompt for your assistant**

> I want to try a backup route for a fictional headphone configurator. The result needs to change the color and rotate the view. Use https://inematds.github.io/ia-com-rota-reserva/guia/en/ as context. Suggest a tool and a test I can verify. Say where the data would be processed and how much it might cost. Wait for my approval before using external services or changing settings.

## Technical setup

To try it without installing anything, [download the project ZIP](https://github.com/inematds/ia-com-rota-reserva/archive/refs/heads/main.zip), extract the folder, and double-click `guia/index.html`.

To use a local server, make sure you have [Python 3](https://www.python.org/downloads/). On Windows, open the extracted folder in File Explorer, type `powershell` in the address bar, and press Enter. On macOS or Linux, open a terminal inside the extracted folder. Confirm the installation with `python3 --version` or, on Windows, `py -3 --version`.

```sh
python3 -m http.server 18090 --bind 127.0.0.1
```

On Windows, run `py -3 -m http.server 18090 --bind 127.0.0.1` instead of the command above. The server stays open in the terminal until you press Ctrl+C.

Open `http://127.0.0.1:18090/guia/`. Select **Usage limit** for the primary provider and **Available** for the backup. The log should show two attempts and open a configurator where you can change the finish and rotation. Select **Access denied** to check that the route stops. If both services are temporarily unavailable, the configurator should remain closed.

The local configurator uses CSS and JavaScript and illustrates the video’s product request. Responses and errors are simulated. The simulator’s logic is custom. The illustrative corresponding status codes would be 429 for a usage limit, 503 for temporary unavailability, and 401 or 403 for an authentication or permission problem. A real router’s fallback policy varies by provider, error type, and configuration.

## The process, from start to finish

The reference is [the YouTube demo](https://www.youtube.com/watch?v=wbchejAAe5A). The documentation below was checked on November 19, 2026. The reference video’s script contains chapters that differ from the current file, so the table uses the times observed during playback.

| In the reference | Tool | What to check |
| --- | --- | --- |
| 3:43 to 7:43 | [FreeLLMAPI](https://github.com/tashfeenahmed/freellmapi) | Desktop or local installation, providers, and fallback order. The demo used port 31415. Check your gateway’s port and key. |
| 7:43 | [Claude Desktop with third-party inference](https://support.claude.com/en/articles/18426225-move-from-claude-enterprise-to-claude-desktop-on-a-cloud-provider) | Whether the configuration is available, the gateway URL, and the effective model on configured routes. |
| 10:20 | [Claude Code in the app](https://support.claude.com/en/articles/18466061-move-claude-code-cli-users) | Select a test folder and authorize only the commands you need. In the headphone configurator, test color, material, and rotation after the build. |
| 11:39 | [Claude Code in the terminal](https://code.claude.com/docs/en/llm-gateway) | Point the session to the gateway, select a chain with enabled options, and start with a short request. |
| 13:32 | FreeLLMAPI Playground | The video prototype received a PDF. For a real test, open the downloaded file and check that its contents and format are correct. |
| 15:49 | [Arena Model API](https://platform.arena.ai/docs/api) | Current documentation lists `https://api.arena.ai` for Anthropic clients. Direct access to a model requires paid funds or eligible promotional credit. Check the account before running it. |
| 17:23 | [v0](https://v0.app/pricing) | The Free plan listed seven messages per day when checked on this date. The reference’s credit announcement and choice of Fable 5.2 depend on the offer and account. |

In the demonstrated setup, FreeLLMAPI uses Google AI Studio, Kilo Gateway, OpenRouter, NVIDIA, Z.ai, and Cloudflare Workers AI. The [official README](https://github.com/tashfeenahmed/freellmapi) maintains the current list. After downloading a compatible version from the [releases](https://github.com/tashfeenahmed/freellmapi/releases) page, enable only providers whose terms and possible costs you have checked. Configure at least two in the fallback chain and run the first test with fictional data.

### Try it with real services

1. Install [Claude Code](https://code.claude.com/docs/en/setup) and check `claude --version`. Download [FreeLLMAPI](https://github.com/tashfeenahmed/freellmapi/releases) for your platform. For server installations, use the [official step-by-step guide](https://github.com/tashfeenahmed/freellmapi#quick-start).
2. Open FreeLLMAPI. Under **Keys**, enable two providers you can use and add their keys when required. Check your limits before proceeding. Under **Models → Fallback chains**, create `free-claude-code` if it does not already exist, enable the two models in the desired order, and save. Test it in the **Playground** with a short question and check which option responded.
3. In the FreeLLMAPI dashboard, copy the Anthropic base URL and unified key. The [FreeLLMAPI documentation for clients](https://github.com/tashfeenahmed/freellmapi/blob/main/docs/en/clients/01-agent-clients.md#claude-desktop-third-party-gateway) specifies `http://127.0.0.1:31415` in the app and `http://localhost:3001` in a server installation. Use the origin without `/v1`.
4. In Claude Desktop, if third-party configuration is available, open **Setup → Gateway**. In versions with the menu shown in the reference, use **Help → Troubleshooting → Developer Mode** and then **Developer → Configure third-party inference**. If the menu does not appear, check the requirements for your version and organization. Enter that URL and the unified key with `x-api-key` authentication, test, and save. Check the model mapping in FreeLLMAPI. The **Code** tab inherits the app's third-party configuration.
5. In Claude Code installed separately, open a new Bash session in a test folder and paste the block below with your installation's URL. When you run it, paste the unified key at the hidden prompt. The subshell keeps the variables out of your regular terminal.

If FreeLLMAPI is on Windows, run Claude Code on the same Windows system and use the [PowerShell option in the FreeLLMAPI manual](https://github.com/tashfeenahmed/freellmapi/blob/main/docs/en/clients/01-agent-clients.md#coding-agents). The Bash block below is for macOS and Linux with the router in the same environment.

```bash
(
  export ANTHROPIC_BASE_URL=http://127.0.0.1:31415
  read -rsp 'FreeLLMAPI unified key: ' ANTHROPIC_AUTH_TOKEN
  printf '\n'
  if [ -z "$ANTHROPIC_AUTH_TOKEN" ]; then
    echo 'Enter a key to continue.' >&2
    exit 1
  fi
  export ANTHROPIC_AUTH_TOKEN
  export ANTHROPIC_MODEL=auto:free-claude-code
  claude
)
```

Ask for a one-sentence response and check the router log to see who responded. If the message says the chain is empty, check which models are enabled. If permission is missing, review the key before trying again. Anthropic documents gateway connections, but [does not support Claude Code with non-Claude models](https://code.claude.com/docs/en/llm-gateway). Integration with external providers requires your credentials and was not performed in this project's demonstration. Use fictional data until you have checked the terms, retention, limits, and permissions.

#### Example provider keys

Two reference options for finding API keys

- **Google AI Studio**. Go to [API keys](https://aistudio.google.com/apikey), create a key, and select Google AI Studio under **Keys → Add key** in FreeLLMAPI. Check first that billing is enabled for your Google project.
- **NVIDIA**. Choose a model in the [NVIDIA catalog](https://build.nvidia.com/explore/discover), sign in to your account, and use **Get API Key** as described in the [official guide](https://docs.api.nvidia.com/nim/re/docs/api-quickstart). Select NVIDIA under **Keys → Add key**.

These keys let FreeLLMAPI communicate with each service. The unified key is different: it acts as your application's password for communicating with FreeLLMAPI. The gateway is the router address that forwards requests. Use the base URL shown in the dashboard, without adding `/v1`.
