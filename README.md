
# 🖤🖊 WebCLI - Lousa

─────────────────────────────
🌐 CLI profissional para gerenciamento de aplicações web em PHP
─────────────────────────────

**Funcionalidades:**  
- 🚀 Iniciar servidor local (porta configurável)  
- 🔨 Build de assets (Webpack/Vite)  
- ⬆ Deploy local/remoto via SSH  
- 📦 Composer install/update  
- 🔧 Auto-update da CLI  
- ⚡ Hooks pré/pós execução  
- 🧩 Comandos customizados e plugins externos  
- 📝 Logging avançado (cores, emojis, timestamps)

─────────────────────────────
💻 Requisitos
─────────────────────────────
- PHP >= 8.0
- Composer
- Windows, Linux, macOS
- Opcional: Docker/K8s ou CI/CD

─────────────────────────────
📦 Instalação
─────────────────────────────
```bash
composer require kseven/web-cli
vendor/bin/webcli <comando>

# Linux/macOS global
sudo ln -s $(pwd)/vendor/bin/webcli /usr/local/bin/webcli
```

─────────────────────────────
📂 Estrutura
─────────────────────────────
```
web-cli/
├─ bin/webcli
├─ src/
│  ├─ Commands/
│  │  ├─ ServeCommand.php
│  │  ├─ BuildCommand.php
│  │  ├─ DeployCommand.php
│  │  ├─ ComposerInstallCommand.php
│  │  ├─ ComposerUpdateCommand.php
│  │  └─ UpdateCommand.php
│  ├─ Contracts/
│  └─ Utils/
├─ user-commands/
├─ plugins/
├─ logs/
├─ tests/
├─ composer.json
└─ README.md
```

─────────────────────────────
⚡ Comandos Core
─────────────────────────────
| Comando               | Alias | Descrição                          |
|-----------------------|-------|-----------------------------------|
| serve                 | -     | Inicia servidor local              |
| build                 | -     | Compila assets                     |
| deploy                | -     | Deploy local/remoto via SSH        |
| composer:install      | ci    | Instala dependências via Composer  |
| composer:update       | cu    | Atualiza dependências via Composer |
| update                | wu    | Atualiza a própria CLI             |
| list                  | -     | Lista todos os comandos            |
| help <comando>        | -     | Exibe ajuda detalhada              |

─────────────────────────────
📌 Cheatsheet
─────────────────────────────
### 🚀 Servidor
```bash
webcli serve
```
Saída:
```
[INFO][timestamp] 🚀 Iniciando servidor na porta 8080
[INFO][timestamp] 🌐 Acesse: http://127.0.0.1:8080
[WARNING][timestamp] ⚠ Porta em uso, usando 8081
[INFO][timestamp] ✅ Servidor iniciado!
```

### 🔨 Build
```bash
webcli build
```
Saída:
```
[INFO][timestamp] 🔨 Iniciando build...
[INFO][timestamp] ⏳ Hook pre-build
[INFO][timestamp] 🛠 Compilando...
[INFO][timestamp] ✅ Build concluído!
[INFO][timestamp] ✨ Hook post-build
```

### ⬆ Deploy
```bash
webcli deploy
```
Saída:
```
[INFO][timestamp] 🚀 Deploy staging...
[INFO][timestamp] 🔑 Autenticando token
[INFO][timestamp] ⬆ Transferindo arquivos
[INFO][timestamp] ✅ Deploy concluído! 🌟
```

### 📦 Composer
```bash
webcli ci  # install
webcli cu  # update
```

### 🔧 Auto-Update
```bash
webcli update  # ou webcli wu
```
Saída:
```
[INFO][timestamp] 🔧 Hook pré-update...
[INFO][timestamp] 💾 Backup concluído!
[INFO][timestamp] 🚀 Atualizando CLI...
[INFO][timestamp] ✅ Atualização completa! 🎉
[INFO][timestamp] ✨ Hook pós-update
```

─────────────────────────────
🧩 Hooks
─────────────────────────────
- pre-serve / post-serve  
- pre-build / post-build  
- pre-deploy / post-deploy  
- pre-update / post-update

Exemplo `.webclirc.json`:
```json
{
  "COMMANDS": {
    "pre-update": ["php scripts/backup.php"],
    "post-update": ["php scripts/clear_cache.php"]
  }
}
```

─────────────────────────────
📝 Logging
─────────────────────────────
- Local: `logs/webcli.log`  
- Níveis: INFO / WARNING / ERROR  
- Emojis, cores e timestamp

Exemplo:
```
[INFO][timestamp] 🔨 Iniciando build...
[INFO][timestamp] ✅ Build concluído!
```

─────────────────────────────
🧩 Extensibilidade
─────────────────────────────
- Comandos do usuário: `user-commands/`  
- Plugins via Composer: `composer require vendor/plugin-cli`  
- Namespace PSR-4 customizado

─────────────────────────────
💬 Suporte
─────────────────────────────
- Issues: [GitHub](https://github.com/kseven/web-cli/issues)  
- Source: [GitHub](https://github.com/kseven/web-cli)  
- Docs: [Web](https://kseven.dev.br/docs)

─────────────────────────────
📜 Licença
─────────────────────────────
MIT © K'Seven
