# Relay — versões publicadas

Este repositório guarda **só as versões publicadas** do Relay (instalador, app portátil e extensão). É daqui que o
próprio app confere se há versão nova e se atualiza sozinho.

O **Relay** é um editor baseado no VS Code (VSCodium) que orquestra agentes de IA das suas próprias assinaturas —
Claude (Claude Code), OpenAI (Codex CLI), Gemini (Antigravity CLI) e Meta (Muse Code) — trocando de conta e de provider
sem perder a conversa, com um navegador que a IA controla, uso de cada conta à vista e todos os modelos de cada conta.

## Baixar

Vá em **[Releases](https://github.com/Wmedrado/relay-releases/releases/latest)** e baixe:

| Arquivo | Para quê |
| --- | --- |
| `Relay-<versão>-setup-x64.exe` | **Instalador (recomendado).** Instala para o seu usuário, sem pedir administrador, e o app se atualiza sozinho. |
| `Relay-<versão>-win32-x64.zip` | App portátil: extraia e abra `Relay.exe` (não se atualiza sozinho). |
| `relay-<versão>.vsix` | Só a extensão, para um VS Code ou VSCodium que você já usa. |
| `SHA256SUMS.txt` | Somas SHA-256 para conferir os arquivos. |

Requisitos: Windows 10 ou 11 (x64). O Relay instala os CLIs dos providers pela tela de Contas; o login é o da sua
assinatura, feito pelo CLI oficial de cada um.

## Atualização automática

Ao abrir (e a cada 6 horas), o Relay instalado consulta a última versão deste repositório. Se houver uma mais nova,
aparece uma notificação com **Atualizar agora**: o app baixa o instalador, confere o SHA-256 publicado pelo GitHub,
fecha, instala em silêncio e reabre. Contas, conversas e configurações ficam como estavam.

A consulta é um `GET` anônimo em `https://api.github.com/repos/Wmedrado/relay-releases/releases/latest`; nada é
enviado sobre você. Para desligar: configuração `relay.updates.enabled`. Para verificar na hora: comando
**Relay: Verificar atualizações**.

## Conferir um download

```powershell
Get-FileHash .\Relay-0.0.3-setup-x64.exe -Algorithm SHA256
```

O resultado tem de ser igual à linha do arquivo em `SHA256SUMS.txt`.

O instalador e o app ainda não são assinados digitalmente: o Windows SmartScreen pode avisar na primeira vez
("Mais informações" → "Executar assim mesmo").

## Problemas

Abra uma [issue](https://github.com/Wmedrado/relay-releases/issues) com a versão (Ajuda → Sobre) e o que aconteceu.

Base do app: VSCodium (MIT). Instalador: Inno Setup. Os nomes e logos de Claude, OpenAI, Gemini e Meta são marcas dos
respectivos donos, usados só para identificar o serviço.
