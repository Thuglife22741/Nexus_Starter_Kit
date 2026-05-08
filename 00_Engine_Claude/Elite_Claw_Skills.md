# 🦅 Elite Claw Skills 

## 🌿 Branches Remotas (37 total)

```
origin/HEAD -> origin/main
  origin/dev/rust
  origin/feat/release-0.1.0-readme
  origin/feat/ui-hardening
  origin/feat/uiux-redesign
  origin/fix/plugin-loading-parity
  origin/fix/skill-invoke
  origin/fix/ui-parity
  origin/integration/dori-cleanroom
  origin/main
  origin/merge-parity-to-main
  origin/rcc/ant-tools
  origin/rcc/api
  origin/rcc/cache-tracking
  origin/rcc/cli
  origin/rcc/cost
  origin/rcc/doctor
  origin/rcc/git
  origin/rcc/grok
  origin/rcc/hook-pipeline
  origin/rcc/hooks
  origin/rcc/image
  origin/rcc/jsonl-session
  origin/rcc/memory
  origin/rcc/parity-fix
  origin/rcc/plugins
  origin/rcc/render
  origin/rcc/runtime
  origin/rcc/sandbox
  origin/rcc/subagent
  origin/rcc/telemetry
  origin/rcc/thinking
  origin/rcc/tools
  origin/rcc/ui-polish
  origin/rcc/update
  origin/release/0.1.0
  origin/sigrid/readme-update
```

## 🗂️ Árvore: `origin/fix/ui-parity`

```
.github/FUNDING.yml
.gitignore
CLAW.md
PARITY.md
README.md
assets/clawd-hero.jpeg
assets/instructkr.png
assets/omx/omx-readme-review-1.png
assets/omx/omx-readme-review-2.png
assets/star-history.png
assets/tweet-screenshot.png
assets/wsj-feature.png
rust/.github/workflows/ci.yml
rust/.gitignore
rust/CONTRIBUTING.md
rust/Cargo.lock
rust/Cargo.toml
rust/README.md
rust/crates/api/Cargo.toml
rust/crates/api/src/client.rs
rust/crates/api/src/error.rs
rust/crates/api/src/lib.rs
rust/crates/api/src/providers/claw_provider.rs
rust/crates/api/src/providers/mod.rs
rust/crates/api/src/providers/openai_compat.rs
rust/crates/api/src/sse.rs
rust/crates/api/src/types.rs
rust/crates/api/tests/client_integration.rs
rust/crates/api/tests/openai_compat_integration.rs
rust/crates/api/tests/provider_client_integration.rs
rust/crates/claw-cli/Cargo.toml
rust/crates/claw-cli/src/app.rs
rust/crates/claw-cli/src/args.rs
rust/crates/claw-cli/src/init.rs
rust/crates/claw-cli/src/input.rs
rust/crates/claw-cli/src/main.rs
rust/crates/claw-cli/src/render.rs
rust/crates/claw-cli/tests/prompt_json_transport.rs
rust/crates/commands/Cargo.toml
rust/crates/commands/src/lib.rs
rust/crates/compat-harness/Cargo.toml
rust/crates/compat-harness/src/lib.rs
rust/crates/lsp/Cargo.toml
rust/crates/lsp/src/client.rs
rust/crates/lsp/src/error.rs
rust/crates/lsp/src/lib.rs
rust/crates/lsp/src/manager.rs
rust/crates/lsp/src/types.rs
rust/crates/plugins/Cargo.toml
rust/crates/plugins/bundled/example-bundled/.claw-plugin/plugin.json
rust/crates/plugins/bundled/example-bundled/hooks/post.sh
rust/crates/plugins/bundled/example-bundled/hooks/pre.sh
rust/crates/plugins/bundled/sample-hooks/.claw-plugin/plugin.json
rust/crates/plugins/bundled/sample-hooks/hooks/post.sh
rust/crates/plugins/bundled/sample-hooks/hooks/pre.sh
rust/crates/plugins/src/hooks.rs
rust/crates/plugins/src/lib.rs
rust/crates/runtime/Cargo.toml
rust/crates/runtime/src/bash.rs
rust/crates/runtime/src/bootstrap.rs
rust/crates/runtime/src/compact.rs
rust/crates/runtime/src/config.rs
rust/crates/runtime/src/conversation.rs
rust/crates/runtime/src/file_ops.rs
rust/crates/runtime/src/hooks.rs
rust/crates/runtime/src/json.rs
rust/crates/runtime/src/lib.rs
rust/crates/runtime/src/mcp.rs
rust/crates/runtime/src/mcp_client.rs
rust/crates/runtime/src/mcp_stdio.rs
rust/crates/runtime/src/oauth.rs
rust/crates/runtime/src/permissions.rs
rust/crates/runtime/src/prompt.rs
rust/crates/runtime/src/remote.rs
rust/crates/runtime/src/sandbox.rs
rust/crates/runtime/src/session.rs
rust/crates/runtime/src/skills.rs
rust/crates/runtime/src/sse.rs
rust/crates/runtime/src/usage.rs
rust/crates/server/Cargo.toml
rust/crates/server/src/lib.rs
rust/crates/tools/.gitignore
rust/crates/tools/Cargo.toml
rust/crates/tools/src/lib.rs
rust/docs/releases/0.1.0.md
src/QueryEngine.py
src/Tool.py
src/__init__.py
src/assistant/__init__.py
src/bootstrap/__init__.py
src/bootstrap_graph.py
src/bridge/__init__.py
src/buddy/__init__.py
src/cli/__init__.py
src/command_graph.py
src/commands.py
src/components/__init__.py
src/constants/__init__.py
src/context.py
src/coordinator/__init__.py
src/costHook.py
src/cost_tracker.py
src/deferred_init.py
src/dialogLaunchers.py
src/direct_modes.py
src/entrypoints/__init__.py
src/execution_registry.py
src/history.py
src/hooks/__init__.py
src/ink.py
src/interactiveHelpers.py
src/keybindings/__init__.py
src/main.py
src/memdir/__init__.py
src/migrations/__init__.py
src/models.py
src/moreright/__init__.py
src/native_ts/__init__.py
src/outputStyles/__init__.py
src/parity_audit.py
src/permissions.py
src/plugins/__init__.py
src/port_manifest.py
src/prefetch.py
src/projectOnboardingState.py
src/query.py
src/query_engine.py
src/reference_data/__init__.py
src/reference_data/archive_surface_snapshot.json
src/reference_data/commands_snapshot.json
src/reference_data/subsystems/assistant.json
src/reference_data/subsystems/bootstrap.json
src/reference_data/subsystems/bridge.json
src/reference_data/subsystems/buddy.json
src/reference_data/subsystems/cli.json
src/reference_data/subsystems/components.json
src/reference_data/subsystems/constants.json
src/reference_data/subsystems/coordinator.json
src/reference_data/subsystems/entrypoints.json
src/reference_data/subsystems/hooks.json
src/reference_data/subsystems/keybindings.json
src/reference_data/subsystems/memdir.json
src/reference_data/subsystems/migrations.json
src/reference_data/subsystems/moreright.json
src/reference_data/subsystems/native_ts.json
src/reference_data/subsystems/outputStyles.json
src/reference_data/subsystems/plugins.json
src/reference_data/subsystems/remote.json
src/reference_data/subsystems/schemas.json
src/reference_data/subsystems/screens.json
src/reference_data/subsystems/server.json
src/reference_data/subsystems/services.json
src/reference_data/subsystems/skills.json
src/reference_data/subsystems/state.json
src/reference_data/subsystems/types.json
src/reference_data/subsystems/upstreamproxy.json
src/reference_data/subsystems/utils.json
src/reference_data/subsystems/vim.json
src/reference_data/subsystems/voice.json
src/reference_data/tools_snapshot.json
src/remote/__init__.py
src/remote_runtime.py
src/replLauncher.py
src/runtime.py
src/schemas/__init__.py
src/screens/__init__.py
src/server/__init__.py
src/services/__init__.py
src/session_store.py
src/setup.py
src/skills/__init__.py
src/state/__init__.py
src/system_init.py
src/task.py
src/tasks.py
src/tool_pool.py
src/tools.py
src/transcript.py
src/types/__init__.py
src/upstreamproxy/__init__.py
src/utils/__init__.py
src/vim/__init__.py
src/voice/__init__.py
tests/test_porting_workspace.py
```

## 🗂️ Árvore: `origin/fix/skill-invoke`

```
.github/FUNDING.yml
.gitignore
CLAW.md
PARITY.md
README.md
assets/clawd-hero.jpeg
assets/instructkr.png
assets/omx/omx-readme-review-1.png
assets/omx/omx-readme-review-2.png
assets/star-history.png
assets/tweet-screenshot.png
assets/wsj-feature.png
rust/.github/workflows/ci.yml
rust/.gitignore
rust/CONTRIBUTING.md
rust/Cargo.lock
rust/Cargo.toml
rust/README.md
rust/crates/api/Cargo.toml
rust/crates/api/src/client.rs
rust/crates/api/src/error.rs
rust/crates/api/src/lib.rs
rust/crates/api/src/providers/claw_provider.rs
rust/crates/api/src/providers/mod.rs
rust/crates/api/src/providers/openai_compat.rs
rust/crates/api/src/sse.rs
rust/crates/api/src/types.rs
rust/crates/api/tests/client_integration.rs
rust/crates/api/tests/openai_compat_integration.rs
rust/crates/api/tests/provider_client_integration.rs
rust/crates/claw-cli/Cargo.toml
rust/crates/claw-cli/src/app.rs
rust/crates/claw-cli/src/args.rs
rust/crates/claw-cli/src/init.rs
rust/crates/claw-cli/src/input.rs
rust/crates/claw-cli/src/main.rs
rust/crates/claw-cli/src/render.rs
rust/crates/commands/Cargo.toml
rust/crates/commands/src/lib.rs
rust/crates/compat-harness/Cargo.toml
rust/crates/compat-harness/src/lib.rs
rust/crates/lsp/Cargo.toml
rust/crates/lsp/src/client.rs
rust/crates/lsp/src/error.rs
rust/crates/lsp/src/lib.rs
rust/crates/lsp/src/manager.rs
rust/crates/lsp/src/types.rs
rust/crates/plugins/Cargo.toml
rust/crates/plugins/bundled/example-bundled/.claw-plugin/plugin.json
rust/crates/plugins/bundled/example-bundled/hooks/post.sh
rust/crates/plugins/bundled/example-bundled/hooks/pre.sh
rust/crates/plugins/bundled/sample-hooks/.claw-plugin/plugin.json
rust/crates/plugins/bundled/sample-hooks/hooks/post.sh
rust/crates/plugins/bundled/sample-hooks/hooks/pre.sh
rust/crates/plugins/src/hooks.rs
rust/crates/plugins/src/lib.rs
rust/crates/runtime/Cargo.toml
rust/crates/runtime/src/bash.rs
rust/crates/runtime/src/bootstrap.rs
rust/crates/runtime/src/compact.rs
rust/crates/runtime/src/config.rs
rust/crates/runtime/src/conversation.rs
rust/crates/runtime/src/file_ops.rs
rust/crates/runtime/src/hooks.rs
rust/crates/runtime/src/json.rs
rust/crates/runtime/src/lib.rs
rust/crates/runtime/src/mcp.rs
rust/crates/runtime/src/mcp_client.rs
rust/crates/runtime/src/mcp_stdio.rs
rust/crates/runtime/src/oauth.rs
rust/crates/runtime/src/permissions.rs
rust/crates/runtime/src/prompt.rs
rust/crates/runtime/src/remote.rs
rust/crates/runtime/src/sandbox.rs
rust/crates/runtime/src/session.rs
rust/crates/runtime/src/sse.rs
rust/crates/runtime/src/usage.rs
rust/crates/server/Cargo.toml
rust/crates/server/src/lib.rs
rust/crates/tools/.gitignore
rust/crates/tools/Cargo.toml
rust/crates/tools/src/lib.rs
rust/docs/releases/0.1.0.md
src/QueryEngine.py
src/Tool.py
src/__init__.py
src/assistant/__init__.py
src/bootstrap/__init__.py
src/bootstrap_graph.py
src/bridge/__init__.py
src/buddy/__init__.py
src/cli/__init__.py
src/command_graph.py
src/commands.py
src/components/__init__.py
src/constants/__init__.py
src/context.py
src/coordinator/__init__.py
src/costHook.py
src/cost_tracker.py
src/deferred_init.py
src/dialogLaunchers.py
src/direct_modes.py
src/entrypoints/__init__.py
src/execution_registry.py
src/history.py
src/hooks/__init__.py
src/ink.py
src/interactiveHelpers.py
src/keybindings/__init__.py
src/main.py
src/memdir/__init__.py
src/migrations/__init__.py
src/models.py
src/moreright/__init__.py
src/native_ts/__init__.py
src/outputStyles/__init__.py
src/parity_audit.py
src/permissions.py
src/plugins/__init__.py
src/port_manifest.py
src/prefetch.py
src/projectOnboardingState.py
src/query.py
src/query_engine.py
src/reference_data/__init__.py
src/reference_data/archive_surface_snapshot.json
src/reference_data/commands_snapshot.json
src/reference_data/subsystems/assistant.json
src/reference_data/subsystems/bootstrap.json
src/reference_data/subsystems/bridge.json
src/reference_data/subsystems/buddy.json
src/reference_data/subsystems/cli.json
src/reference_data/subsystems/components.json
src/reference_data/subsystems/constants.json
src/reference_data/subsystems/coordinator.json
src/reference_data/subsystems/entrypoints.json
src/reference_data/subsystems/hooks.json
src/reference_data/subsystems/keybindings.json
src/reference_data/subsystems/memdir.json
src/reference_data/subsystems/migrations.json
src/reference_data/subsystems/moreright.json
src/reference_data/subsystems/native_ts.json
src/reference_data/subsystems/outputStyles.json
src/reference_data/subsystems/plugins.json
src/reference_data/subsystems/remote.json
src/reference_data/subsystems/schemas.json
src/reference_data/subsystems/screens.json
src/reference_data/subsystems/server.json
src/reference_data/subsystems/services.json
src/reference_data/subsystems/skills.json
src/reference_data/subsystems/state.json
src/reference_data/subsystems/types.json
src/reference_data/subsystems/upstreamproxy.json
src/reference_data/subsystems/utils.json
src/reference_data/subsystems/vim.json
src/reference_data/subsystems/voice.json
src/reference_data/tools_snapshot.json
src/remote/__init__.py
src/remote_runtime.py
src/replLauncher.py
src/runtime.py
src/schemas/__init__.py
src/screens/__init__.py
src/server/__init__.py
src/services/__init__.py
src/session_store.py
src/setup.py
src/skills/__init__.py
src/state/__init__.py
src/system_init.py
src/task.py
src/tasks.py
src/tool_pool.py
src/tools.py
src/transcript.py
src/types/__init__.py
src/upstreamproxy/__init__.py
src/utils/__init__.py
src/vim/__init__.py
src/voice/__init__.py
tests/test_porting_workspace.py
```


## 📄 Código: `origin/fix/ui-parity:src/commands.py`

```python
from __future__ import annotations

import json
from dataclasses import dataclass
from functools import lru_cache
from pathlib import Path

from .models import PortingBacklog, PortingModule

SNAPSHOT_PATH = Path(__file__).resolve().parent / 'reference_data' / 'commands_snapshot.json'


@dataclass(frozen=True)
class CommandExecution:
    name: str
    source_hint: str
    prompt: str
    handled: bool
    message: str


@lru_cache(maxsize=1)
def load_command_snapshot() -> tuple[PortingModule, ...]:
    raw_entries = json.loads(SNAPSHOT_PATH.read_text())
    return tuple(
        PortingModule(
            name=entry['name'],
            responsibility=entry['responsibility'],
            source_hint=entry['source_hint'],
            status='mirrored',
        )
        for entry in raw_entries
    )


PORTED_COMMANDS = load_command_snapshot()


@lru_cache(maxsize=1)
def built_in_command_names() -> frozenset[str]:
    return frozenset(module.name for module in PORTED_COMMANDS)


def build_command_backlog() -> PortingBacklog:
    return PortingBacklog(title='Command surface', modules=list(PORTED_COMMANDS))


def command_names() -> list[str]:
    return [module.name for module in PORTED_COMMANDS]


def get_command(name: str) -> PortingModule | None:
    needle = name.lower()
    for module in PORTED_COMMANDS:
        if module.name.lower() == needle:
            return module
    return None


def get_commands(cwd: str | None = None, include_plugin_commands: bool = True, include_skill_commands: bool = True) -> tuple[PortingModule, ...]:
    commands = list(PORTED_COMMANDS)
    if not include_plugin_commands:
        commands = [module for module in commands if 'plugin' not in module.source_hint.lower()]
    if not include_skill_commands:
        commands = [module for module in commands if 'skills' not in module.source_hint.lower()]
    return tuple(commands)


def find_commands(query: str, limit: int = 20) -> list[PortingModule]:
    needle = query.lower()
    matches = [module for module in PORTED_COMMANDS if needle in module.name.lower() or needle in module.source_hint.lower()]
    return matches[:limit]


def execute_command(name: str, prompt: str = '') -> CommandExecution:
    module = get_command(name)
    if module is None:
        return CommandExecution(name=name, source_hint='', prompt=prompt, handled=False, message=f'Unknown mirrored command: {name}')
    action = f"Mirrored command '{module.name}' from {module.source_hint} would handle prompt {prompt!r}."
    return CommandExecution(name=module.name, source_hint=module.source_hint, prompt=prompt, handled=True, message=action)


def render_command_index(limit: int = 20, query: str | None = None) -> str:
    modules = find_commands(query, limit) if query else list(PORTED_COMMANDS[:limit])
    lines = [f'Command entries: {len(PORTED_COMMANDS)}', '']
    if query:
        lines.append(f'Filtered by: {query}')
        lines.append('')
    lines.extend(f'- {module.name} — {module.source_hint}' for module in modules)
    return '\n'.join(lines)
```

---

## 📄 Código: `origin/fix/skill-invoke:src/commands.py`

```python
from __future__ import annotations

import json
from dataclasses import dataclass
from functools import lru_cache
from pathlib import Path

from .models import PortingBacklog, PortingModule

SNAPSHOT_PATH = Path(__file__).resolve().parent / 'reference_data' / 'commands_snapshot.json'


@dataclass(frozen=True)
class CommandExecution:
    name: str
    source_hint: str
    prompt: str
    handled: bool
    message: str


@lru_cache(maxsize=1)
def load_command_snapshot() -> tuple[PortingModule, ...]:
    raw_entries = json.loads(SNAPSHOT_PATH.read_text())
    return tuple(
        PortingModule(
            name=entry['name'],
            responsibility=entry['responsibility'],
            source_hint=entry['source_hint'],
            status='mirrored',
        )
        for entry in raw_entries
    )


PORTED_COMMANDS = load_command_snapshot()


@lru_cache(maxsize=1)
def built_in_command_names() -> frozenset[str]:
    return frozenset(module.name for module in PORTED_COMMANDS)


def build_command_backlog() -> PortingBacklog:
    return PortingBacklog(title='Command surface', modules=list(PORTED_COMMANDS))


def command_names() -> list[str]:
    return [module.name for module in PORTED_COMMANDS]


def get_command(name: str) -> PortingModule | None:
    needle = name.lower()
    for module in PORTED_COMMANDS:
        if module.name.lower() == needle:
            return module
    return None


def get_commands(cwd: str | None = None, include_plugin_commands: bool = True, include_skill_commands: bool = True) -> tuple[PortingModule, ...]:
    commands = list(PORTED_COMMANDS)
    if not include_plugin_commands:
        commands = [module for module in commands if 'plugin' not in module.source_hint.lower()]
    if not include_skill_commands:
        commands = [module for module in commands if 'skills' not in module.source_hint.lower()]
    return tuple(commands)


def find_commands(query: str, limit: int = 20) -> list[PortingModule]:
    needle = query.lower()
    matches = [module for module in PORTED_COMMANDS if needle in module.name.lower() or needle in module.source_hint.lower()]
    return matches[:limit]


def execute_command(name: str, prompt: str = '') -> CommandExecution:
    module = get_command(name)
    if module is None:
        return CommandExecution(name=name, source_hint='', prompt=prompt, handled=False, message=f'Unknown mirrored command: {name}')
    action = f"Mirrored command '{module.name}' from {module.source_hint} would handle prompt {prompt!r}."
    return CommandExecution(name=module.name, source_hint=module.source_hint, prompt=prompt, handled=True, message=action)


def render_command_index(limit: int = 20, query: str | None = None) -> str:
    modules = find_commands(query, limit) if query else list(PORTED_COMMANDS[:limit])
    lines = [f'Command entries: {len(PORTED_COMMANDS)}', '']
    if query:
        lines.append(f'Filtered by: {query}')
        lines.append('')
    lines.extend(f'- {module.name} — {module.source_hint}' for module in modules)
    return '\n'.join(lines)
```

---

## 🧠 Skills & Padrões Extraídos do `commands.py`

### 🧩 Snapshot-Based Command Registry
- **Fonte:** `load_command_snapshot() + @lru_cache(maxsize=1)`
- **Descrição:** JSON snapshot lido uma única vez do disco via `lru_cache`. Retorna `tuple` imutável de `PortingModule`. Zero overhead de I/O após primeira carga. Thread-safe.
- **Padrão:** ``SNAPSHOT_PATH → json.loads() → tuple(PortingModule(...))``

### 🧩 Filtro Composicional de Comandos
- **Fonte:** `get_commands(cwd, include_plugin_commands, include_skill_commands)`
- **Descrição:** Copia a lista global `PORTED_COMMANDS` sem mutação. Aplica filtros booleanos encadeados via `source_hint`. API limpa e composível.
- **Padrão:** ``commands = list(PORTED_COMMANDS)` → filter by source_hint flags`

### 🧩 Execução com Feedback Estruturado
- **Fonte:** `execute_command(name, prompt) → CommandExecution`
- **Descrição:** None-guard explícito antes de qualquer operação. Retorna frozen dataclass com `handled: bool`. O caller decide o que fazer sem try/except.
- **Padrão:** ``get_command(name)` → None check → `CommandExecution(handled=True/False)``

### 🧩 Render Index CLI-Ready
- **Fonte:** `render_command_index(limit, query)`
- **Descrição:** Query opcional via `find_commands()`. Slice direto quando sem query. Output string pura, zero dependências de UI ou framework.
- **Padrão:** ``find_commands(query, limit) if query else PORTED_COMMANDS[:limit]``

### 🧩 Case-Insensitive Lookup com Busca Parcial
- **Fonte:** `get_command() · find_commands()`
- **Descrição:** `needle = query.lower()` aplicado a `name` e `source_hint`. Suporte a lookup exato (get_command) e busca parcial com limite configurável.
- **Padrão:** ``needle in module.name.lower() or needle in module.source_hint.lower()``

### 🧩 Frozen Dataclass como Contrato Imutável de Saída
- **Fonte:** `@dataclass(frozen=True) class CommandExecution`
- **Descrição:** Dataclass imutável com campos tipados (str + bool). Garante que o resultado nunca seja modificado acidentalmente após o retorno.
- **Padrão:** ``@dataclass(frozen=True)` — name, source_hint, prompt, handled, message`

### 🧩 built_in_command_names como frozenset Cacheado
- **Fonte:** `built_in_command_names() → frozenset[str]`
- **Descrição:** Conjunto imutável de nomes de comandos built-in, gerado via `lru_cache`. Lookup O(1) para verificar se um nome é built-in.
- **Padrão:** ``frozenset(module.name for module in PORTED_COMMANDS)``

---

> _"Nexus.AI: Elevando a produtividade com inteligência e engenharia de elite."_


