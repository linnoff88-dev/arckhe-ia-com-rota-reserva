# IA com Rota Reserva

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="48" />
  <p><strong>Arckhé AI</strong></p>
</div>


[![IA com Rota Reserva](guia/assets/hero.jpg)](https://linnoff88-dev.github.io/

**[PortuguêÂªs](README.md) êÂ· [English](README.en.md) êÂ· [EspaêÂ±ol](README.es.md)**

[Abra o guia e teste a rota reserva](https://linnoff88-dev.github.io/

ê°Å¸Å½Â¬ [VêÂ­deo em portuguêÂªs](https://www.youtube.com/watch?v=R_Mf8iMYAQk)

## O que êÂ©

IA com Rota Reserva êÂ© um guia com uma demonstraêÂ§êÂ£o para quem quer experimentar ferramentas de IA com limites de uso. Ele mostra como o FreeLLMAPI tenta outro provedor, o serviêÂ§o que recebe seu pedido e fornece o modelo, e onde entram Claude Desktop, Claude Code, Arena e v0. VocêÂª pode comeêÂ§ar pela demonstraêÂ§êÂ£o, que roda no navegador e usa respostas fictêÂ­cias.

**Pedido para seu assistente**

> Quero experimentar uma rota reserva para um configurador fictêÂ­cio de fones. O resultado precisa mudar a cor e girar a vista. Use como contexto https://linnoff88-dev.github.io/ . Sugira uma ferramenta e um teste que eu consiga conferir. Diga onde os dados seriam processados e quanto poderia custar. Aguarde meu aval antes de usar serviêÂ§os externos ou alterar configuraêÂ§êÂµes.

## InstalaêÂ§êÂ£o têÂ©cnica

Para testar sem instalar nada, [baixe o ZIP do projeto](https://github.com/linnoff88-dev/ia-com-rota-reserva/archive/refs/heads/main.zip), extraia a pasta e dêÂª dois cliques em `guia/index.html`.

Para usar um servidor local, confirme que tem [Python 3](https://www.python.org/downloads/). No Windows, abra a pasta extraêÂ­da no Explorador de Arquivos, digite `powershell` na barra de endereêÂ§o e pressione Enter. No macOS ou Linux, abra o terminal dentro da pasta extraêÂ­da. Confirme a instalaêÂ§êÂ£o com `python3 --version` ou `py -3 --version` no Windows.

```sh
python3 -m http.server 18090 --bind 127.0.0.1
```

No Windows, execute `py -3 -m http.server 18090 --bind 127.0.0.1` no lugar do comando acima. O servidor fica aberto no terminal atêÂ© vocêÂª pressionar Ctrl+C.

Abra `http://127.0.0.1:18090/guia/`. Selecione **Limite de uso** no principal e **DisponêÂ­vel** na reserva. O registro deve mostrar duas tentativas e abrir um configurador em que vocêÂª consegue mudar acabamento e rotaêÂ§êÂ£o. Selecione **Acesso negado** para verificar a interrupêÂ§êÂ£o da rota. Com os dois serviêÂ§os temporariamente indisponêÂ­veis, o configurador deve permanecer fechado.

O configurador local usa CSS e JavaScript e exemplifica o pedido de produto do vêÂ­deo. As respostas e os erros sêÂ£o simulados. A lêÂ³gica do simulador êÂ© prêÂ³pria. Os cêÂ³digos ilustrativos correspondentes seriam 429 para limite de uso, 503 para indisponibilidade temporêÂ¡ria e 401 ou 403 para um problema de autenticaêÂ§êÂ£o ou permissêÂ£o. A polêÂ­tica de fallback de um roteador real varia por provedor, tipo de erro e configuraêÂ§êÂ£o.

## O processo, do inêÂ­cio ao fim

A referêÂªncia êÂ© [a demonstraêÂ§êÂ£o no YouTube](https://www.youtube.com/watch?v=wbchejAAe5A). A documentaêÂ§êÂ£o abaixo foi conferida em 19 de novembro de 2026. O roteiro do vêÂ­deo de referêÂªncia contêÂ©m capêÂ­tulos que divergem do arquivo atual, por isso a tabela usa os tempos da reproduêÂ§êÂ£o observada.

| Na referêÂªncia | Ferramenta | O que conferir |
| --- | --- | --- |
| 3:43 a 7:43 | [FreeLLMAPI](https://github.com/tashfeenahmed/freellmapi) | Desktop ou instalaêÂ§êÂ£o local, provedores e ordem de fallback. A porta na demo era 31415. Confira a porta e a chave do seu gateway. |
| 7:43 | [Claude Desktop com inferêÂªncia de terceiros](https://support.claude.com/en/articles/18426225-move-from-claude-enterprise-to-claude-desktop-on-a-cloud-provider) | Disponibilidade da configuraêÂ§êÂ£o, URL do gateway e modelo efetivo nas rotas configuradas. |
| 10:20 | [Claude Code no aplicativo](https://support.claude.com/en/articles/18466061-move-claude-code-cli-users) | Selecione uma pasta de teste e autorize sêÂ³ os comandos necessêÂ¡rios. No configurador de fones, teste cor, material e rotaêÂ§êÂ£o apêÂ³s o build. |
| 11:39 | [Claude Code no terminal](https://code.claude.com/docs/en/llm-gateway) | Aponte a sessêÂ£o para o gateway, selecione uma cadeia com opêÂ§êÂµes habilitadas e envie primeiro um pedido curto. |
| 13:32 | FreeLLMAPI Playground | O protêÂ³tipo do vêÂ­deo recebia um PDF. Em um teste real, abra o arquivo baixado e verifique se o conteêÂºdo e o formato conferem. |
| 15:49 | [Arena Model API](https://platform.arena.ai/docs/api) | A documentaêÂ§êÂ£o atual indica `https://api.arena.ai` para clientes Anthropic. O acesso direto a um modelo requer fundos pagos ou crêÂ©dito promocional elegêÂ­vel. Consulte a conta antes de executar. |
| 17:23 | [v0](https://v0.app/pricing) | O plano Free lista sete mensagens por dia na consulta desta data. O anêÂºncio de crêÂ©dito da referêÂªncia e a escolha de Fable 5.2 dependem da oferta e da conta. |

Na instalaêÂ§êÂ£o demonstrada, o FreeLLMAPI usa Google AI Studio, Kilo Gateway, OpenRouter, NVIDIA, Z.ai e Cloudflare Workers AI. O [README oficial](https://github.com/tashfeenahmed/freellmapi) mantêÂ©m a lista atual. Depois de baixar uma versêÂ£o compatêÂ­vel pela pêÂ¡gina de [releases](https://github.com/tashfeenahmed/freellmapi/releases), habilite apenas provedores cujos termos e possêÂ­veis custos vocêÂª tenha conferido. Configure pelo menos dois na cadeia de fallback e faêÂ§a o primeiro teste com dados fictêÂ­cios.

### Experimente com serviêÂ§os reais

1. Instale [Claude Code](https://code.claude.com/docs/en/setup) e confira `claude --version`. Baixe o [FreeLLMAPI](https://github.com/tashfeenahmed/freellmapi/releases) para sua plataforma. Em instalaêÂ§êÂµes de servidor, use o [passo a passo oficial](https://github.com/tashfeenahmed/freellmapi#quick-start).
2. Abra o FreeLLMAPI. Em **Keys**, habilite dois provedores que vocêÂª pode usar e cadastre as chaves quando exigidas. Confira seus limites antes de prosseguir. Em **Models ê¢â â Fallback chains**, crie `free-claude-code` se ainda nêÂ£o existir, habilite os dois modelos na ordem desejada e salve. Teste no **Playground** com uma pergunta curta e confira qual opêÂ§êÂ£o respondeu.
3. No painel do FreeLLMAPI, copie a URL base Anthropic e a chave unificada. A [documentaêÂ§êÂ£o do FreeLLMAPI para clientes](https://github.com/tashfeenahmed/freellmapi/blob/main/docs/en/clients/01-agent-clients.md#claude-desktop-third-party-gateway) indica `http://127.0.0.1:31415` no app e `http://localhost:3001` na instalaêÂ§êÂ£o de servidor. Use a origem sem `/v1`.
4. No Claude Desktop, se a configuraêÂ§êÂ£o de terceiros estiver disponêÂ­vel, abra **Setup ê¢â â Gateway**. Em versêÂµes com o menu da referêÂªncia, use **Help ê¢â â Troubleshooting ê¢â â Developer Mode** e depois **Developer ê¢â â Configure third-party inference**. Se o menu nêÂ£o aparecer, verifique as exigêÂªncias da versêÂ£o e da sua organizaêÂ§êÂ£o. Use essa URL e a chave unificada com autenticaêÂ§êÂ£o `x-api-key`, teste e salve. Confira o mapeamento de modelos no FreeLLMAPI. A aba **Code** herda a configuraêÂ§êÂ£o de terceiros da aplicaêÂ§êÂ£o.
5. No Claude Code instalado separadamente, abra uma nova sessêÂ£o Bash em uma pasta de teste e cole o bloco abaixo com a URL da sua instalaêÂ§êÂ£o. Ao executar, cole a chave unificada no prompt oculto. A subsessêÂ£o mantêÂ©m as variêÂ¡veis fora do seu terminal normal.

Se o FreeLLMAPI estiver no Windows, execute o Claude Code no mesmo Windows e use a opêÂ§êÂ£o [PowerShell do manual do FreeLLMAPI](https://github.com/tashfeenahmed/freellmapi/blob/main/docs/en/clients/01-agent-clients.md#coding-agents). O bloco Bash abaixo serve a macOS e Linux com o roteador no mesmo ambiente.

```bash
(
  export ANTHROPIC_BASE_URL=http://127.0.0.1:31415
  read -rsp 'Chave unificada do FreeLLMAPI: ' ANTHROPIC_AUTH_TOKEN
  printf '\n'
  if [ -z "$ANTHROPIC_AUTH_TOKEN" ]; then
    echo 'Informe uma chave para continuar.' >&2
    exit 1
  fi
  export ANTHROPIC_AUTH_TOKEN
  export ANTHROPIC_MODEL=auto:free-claude-code
  claude
)
```

PeêÂ§a uma resposta de uma frase e confira no registro do roteador quem respondeu. Se a mensagem disser que a cadeia estêÂ¡ vazia, confira os modelos habilitados. Se faltar permissêÂ£o, revise a chave antes de insistir. A Anthropic documenta a conexêÂ£o por gateway, porêÂ©m [nêÂ£o oferece suporte para Claude Code com modelos que nêÂ£o sejam Claude](https://code.claude.com/docs/en/llm-gateway). A integraêÂ§êÂ£o com provedores externos exige as suas credenciais e nêÂ£o foi executada na demonstraêÂ§êÂ£o deste projeto. Use dados fictêÂ­cios atêÂ© verificar termos, retenêÂ§êÂ£o, limites e permissêÂµes.

#### Exemplos de chaves

Duas opêÂ§êÂµes da referêÂªncia para encontrar as chaves

- **Google AI Studio**. Entre em [API keys](https://aistudio.google.com/apikey), crie uma chave e selecione Google AI Studio em **Keys ê¢â â Add key** no FreeLLMAPI. Confira antes se seu projeto Google tem cobranêÂ§a habilitada.
- **NVIDIA**. Escolha um modelo no [catêÂ¡logo da NVIDIA](https://build.nvidia.com/explore/discover), entre na sua conta e use **Get API Key** conforme o [guia oficial](https://docs.api.nvidia.com/nim/re/docs/api-quickstart). Selecione NVIDIA em **Keys ê¢â â Add key**.

Essas chaves permitem que o FreeLLMAPI fale com cada serviêÂ§o. A chave unificada êÂ© outra: funciona como a senha do seu aplicativo para falar com o FreeLLMAPI. O gateway êÂ© o endereêÂ§o do roteador que faz o encaminhamento. Use a URL base exibida no painel, sem acrescentar o trecho `/v1`.

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>