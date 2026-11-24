# IA com Rota Reserva

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="48" />
  <p><strong>Arckhé AI</strong></p>
</div>


[![IA com Rota Reserva](guia/assets/hero.jpg)](https://linnoff88-dev.github.io/

**[PortuguÃªs](README.md) Â· [English](README.en.md) Â· [EspaÃ±ol](README.es.md)**

[Abra o guia e teste a rota reserva](https://linnoff88-dev.github.io/

ðŸŽ¬ [VÃ­deo em portuguÃªs](https://www.youtube.com/watch?v=R_Mf8iMYAQk)

## O que Ã©

IA com Rota Reserva Ã© um guia com uma demonstraÃ§Ã£o para quem quer experimentar ferramentas de IA com limites de uso. Ele mostra como o FreeLLMAPI tenta outro provedor, o serviÃ§o que recebe seu pedido e fornece o modelo, e onde entram Claude Desktop, Claude Code, Arena e v0. VocÃª pode comeÃ§ar pela demonstraÃ§Ã£o, que roda no navegador e usa respostas fictÃ­cias.

**Pedido para seu assistente**

> Quero experimentar uma rota reserva para um configurador fictÃ­cio de fones. O resultado precisa mudar a cor e girar a vista. Use como contexto https://linnoff88-dev.github.io/ . Sugira uma ferramenta e um teste que eu consiga conferir. Diga onde os dados seriam processados e quanto poderia custar. Aguarde meu aval antes de usar serviÃ§os externos ou alterar configuraÃ§Ãµes.

## InstalaÃ§Ã£o tÃ©cnica

Para testar sem instalar nada, [baixe o ZIP do projeto](https://github.com/linnoff88-dev/ia-com-rota-reserva/archive/refs/heads/main.zip), extraia a pasta e dÃª dois cliques em `guia/index.html`.

Para usar um servidor local, confirme que tem [Python 3](https://www.python.org/downloads/). No Windows, abra a pasta extraÃ­da no Explorador de Arquivos, digite `powershell` na barra de endereÃ§o e pressione Enter. No macOS ou Linux, abra o terminal dentro da pasta extraÃ­da. Confirme a instalaÃ§Ã£o com `python3 --version` ou `py -3 --version` no Windows.

```sh
python3 -m http.server 18090 --bind 127.0.0.1
```

No Windows, execute `py -3 -m http.server 18090 --bind 127.0.0.1` no lugar do comando acima. O servidor fica aberto no terminal atÃ© vocÃª pressionar Ctrl+C.

Abra `http://127.0.0.1:18090/guia/`. Selecione **Limite de uso** no principal e **DisponÃ­vel** na reserva. O registro deve mostrar duas tentativas e abrir um configurador em que vocÃª consegue mudar acabamento e rotaÃ§Ã£o. Selecione **Acesso negado** para verificar a interrupÃ§Ã£o da rota. Com os dois serviÃ§os temporariamente indisponÃ­veis, o configurador deve permanecer fechado.

O configurador local usa CSS e JavaScript e exemplifica o pedido de produto do vÃ­deo. As respostas e os erros sÃ£o simulados. A lÃ³gica do simulador Ã© prÃ³pria. Os cÃ³digos ilustrativos correspondentes seriam 429 para limite de uso, 503 para indisponibilidade temporÃ¡ria e 401 ou 403 para um problema de autenticaÃ§Ã£o ou permissÃ£o. A polÃ­tica de fallback de um roteador real varia por provedor, tipo de erro e configuraÃ§Ã£o.

## O processo, do inÃ­cio ao fim

A referÃªncia Ã© [a demonstraÃ§Ã£o no YouTube](https://www.youtube.com/watch?v=wbchejAAe5A). A documentaÃ§Ã£o abaixo foi conferida em 19 de novembro de 2026. O roteiro do vÃ­deo de referÃªncia contÃ©m capÃ­tulos que divergem do arquivo atual, por isso a tabela usa os tempos da reproduÃ§Ã£o observada.

| Na referÃªncia | Ferramenta | O que conferir |
| --- | --- | --- |
| 3:43 a 7:43 | [FreeLLMAPI](https://github.com/tashfeenahmed/freellmapi) | Desktop ou instalaÃ§Ã£o local, provedores e ordem de fallback. A porta na demo era 31415. Confira a porta e a chave do seu gateway. |
| 7:43 | [Claude Desktop com inferÃªncia de terceiros](https://support.claude.com/en/articles/18426225-move-from-claude-enterprise-to-claude-desktop-on-a-cloud-provider) | Disponibilidade da configuraÃ§Ã£o, URL do gateway e modelo efetivo nas rotas configuradas. |
| 10:20 | [Claude Code no aplicativo](https://support.claude.com/en/articles/18466061-move-claude-code-cli-users) | Selecione uma pasta de teste e autorize sÃ³ os comandos necessÃ¡rios. No configurador de fones, teste cor, material e rotaÃ§Ã£o apÃ³s o build. |
| 11:39 | [Claude Code no terminal](https://code.claude.com/docs/en/llm-gateway) | Aponte a sessÃ£o para o gateway, selecione uma cadeia com opÃ§Ãµes habilitadas e envie primeiro um pedido curto. |
| 13:32 | FreeLLMAPI Playground | O protÃ³tipo do vÃ­deo recebia um PDF. Em um teste real, abra o arquivo baixado e verifique se o conteÃºdo e o formato conferem. |
| 15:49 | [Arena Model API](https://platform.arena.ai/docs/api) | A documentaÃ§Ã£o atual indica `https://api.arena.ai` para clientes Anthropic. O acesso direto a um modelo requer fundos pagos ou crÃ©dito promocional elegÃ­vel. Consulte a conta antes de executar. |
| 17:23 | [v0](https://v0.app/pricing) | O plano Free lista sete mensagens por dia na consulta desta data. O anÃºncio de crÃ©dito da referÃªncia e a escolha de Fable 5.2 dependem da oferta e da conta. |

Na instalaÃ§Ã£o demonstrada, o FreeLLMAPI usa Google AI Studio, Kilo Gateway, OpenRouter, NVIDIA, Z.ai e Cloudflare Workers AI. O [README oficial](https://github.com/tashfeenahmed/freellmapi) mantÃ©m a lista atual. Depois de baixar uma versÃ£o compatÃ­vel pela pÃ¡gina de [releases](https://github.com/tashfeenahmed/freellmapi/releases), habilite apenas provedores cujos termos e possÃ­veis custos vocÃª tenha conferido. Configure pelo menos dois na cadeia de fallback e faÃ§a o primeiro teste com dados fictÃ­cios.

### Experimente com serviÃ§os reais

1. Instale [Claude Code](https://code.claude.com/docs/en/setup) e confira `claude --version`. Baixe o [FreeLLMAPI](https://github.com/tashfeenahmed/freellmapi/releases) para sua plataforma. Em instalaÃ§Ãµes de servidor, use o [passo a passo oficial](https://github.com/tashfeenahmed/freellmapi#quick-start).
2. Abra o FreeLLMAPI. Em **Keys**, habilite dois provedores que vocÃª pode usar e cadastre as chaves quando exigidas. Confira seus limites antes de prosseguir. Em **Models â†’ Fallback chains**, crie `free-claude-code` se ainda nÃ£o existir, habilite os dois modelos na ordem desejada e salve. Teste no **Playground** com uma pergunta curta e confira qual opÃ§Ã£o respondeu.
3. No painel do FreeLLMAPI, copie a URL base Anthropic e a chave unificada. A [documentaÃ§Ã£o do FreeLLMAPI para clientes](https://github.com/tashfeenahmed/freellmapi/blob/main/docs/en/clients/01-agent-clients.md#claude-desktop-third-party-gateway) indica `http://127.0.0.1:31415` no app e `http://localhost:3001` na instalaÃ§Ã£o de servidor. Use a origem sem `/v1`.
4. No Claude Desktop, se a configuraÃ§Ã£o de terceiros estiver disponÃ­vel, abra **Setup â†’ Gateway**. Em versÃµes com o menu da referÃªncia, use **Help â†’ Troubleshooting â†’ Developer Mode** e depois **Developer â†’ Configure third-party inference**. Se o menu nÃ£o aparecer, verifique as exigÃªncias da versÃ£o e da sua organizaÃ§Ã£o. Use essa URL e a chave unificada com autenticaÃ§Ã£o `x-api-key`, teste e salve. Confira o mapeamento de modelos no FreeLLMAPI. A aba **Code** herda a configuraÃ§Ã£o de terceiros da aplicaÃ§Ã£o.
5. No Claude Code instalado separadamente, abra uma nova sessÃ£o Bash em uma pasta de teste e cole o bloco abaixo com a URL da sua instalaÃ§Ã£o. Ao executar, cole a chave unificada no prompt oculto. A subsessÃ£o mantÃ©m as variÃ¡veis fora do seu terminal normal.

Se o FreeLLMAPI estiver no Windows, execute o Claude Code no mesmo Windows e use a opÃ§Ã£o [PowerShell do manual do FreeLLMAPI](https://github.com/tashfeenahmed/freellmapi/blob/main/docs/en/clients/01-agent-clients.md#coding-agents). O bloco Bash abaixo serve a macOS e Linux com o roteador no mesmo ambiente.

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

PeÃ§a uma resposta de uma frase e confira no registro do roteador quem respondeu. Se a mensagem disser que a cadeia estÃ¡ vazia, confira os modelos habilitados. Se faltar permissÃ£o, revise a chave antes de insistir. A Anthropic documenta a conexÃ£o por gateway, porÃ©m [nÃ£o oferece suporte para Claude Code com modelos que nÃ£o sejam Claude](https://code.claude.com/docs/en/llm-gateway). A integraÃ§Ã£o com provedores externos exige as suas credenciais e nÃ£o foi executada na demonstraÃ§Ã£o deste projeto. Use dados fictÃ­cios atÃ© verificar termos, retenÃ§Ã£o, limites e permissÃµes.

#### Exemplos de chaves

Duas opÃ§Ãµes da referÃªncia para encontrar as chaves

- **Google AI Studio**. Entre em [API keys](https://aistudio.google.com/apikey), crie uma chave e selecione Google AI Studio em **Keys â†’ Add key** no FreeLLMAPI. Confira antes se seu projeto Google tem cobranÃ§a habilitada.
- **NVIDIA**. Escolha um modelo no [catÃ¡logo da NVIDIA](https://build.nvidia.com/explore/discover), entre na sua conta e use **Get API Key** conforme o [guia oficial](https://docs.api.nvidia.com/nim/re/docs/api-quickstart). Selecione NVIDIA em **Keys â†’ Add key**.

Essas chaves permitem que o FreeLLMAPI fale com cada serviÃ§o. A chave unificada Ã© outra: funciona como a senha do seu aplicativo para falar com o FreeLLMAPI. O gateway Ã© o endereÃ§o do roteador que faz o encaminhamento. Use a URL base exibida no painel, sem acrescentar o trecho `/v1`.

---

<div align="center">
  <img src="capa/logo.svg" alt="Arckhé AI" height="32" />
  <p><strong>Arckhé AI</strong></p>
</div>