<div align="center">

# GitHub Publisher Skill

<p align="center">
  <img src="assets/demo.gif" alt="GitHub Publisher Demo" />
</p>

> *Genera automáticamente documentación profesional de GitHub para cualquier Claude Skill, con un solo comando.*

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)
[![Agent Skills](https://img.shields.io/badge/Agent%20Skills-Standard-green)](https://agentskills.io)
[![skills.sh](https://img.shields.io/badge/skills.sh-Compatible-blue)](https://skills.sh)
[![Multi-Runtime](https://img.shields.io/badge/Runtime-Claude%20Code%20·%20Codex%20·%20Cursor%20·%20Hermes-blueviolet)](#installation)

<br>

**Cada vez que crees un nuevo Skill, un solo comando genera automáticamente documentación profesional según los estándares de código abierto.**

<sub>Basado en el protocolo abierto [Agent Skills](https://agentskills.io), compatible con Claude Code, Codex, Cursor, OpenClaw, Hermes Agent, CodeBuddy, Workbuddy, Gemini CLI, OpenCode y más de 50 runtimes compatibles.</sub>

<br>

[Demo](#demo) · [Instalación](#instalación) · [Uso](#uso) · [Cómo funciona](#cómo-funciona) · [Estructura del proyecto](#estructura-del-proyecto)

<br>

**Otros idiomas / Other Languages:**

[中文](README.md) · [English](README_EN.md) · [日本語](README_JA.md) · [한국어](README_KO.md)

</div>

---

## Demo

```
Usuario    ❯ /publish skills/my-new-skill

GitHub     ❯ Leyendo my-new-skill...
Publisher  ❯ ✅ SKILL.md, scripts/, references/ leídos
            ❯ 📝 Generando README profesional...
            ❯ ✅ README generado
            ❯ 🔍 Control de calidad pasado
            ❯ 📤 Haciendo commit a GitHub...

Usuario    ❯ yes

GitHub     ❯ 🎉 ¡Publicado con éxito!
Publisher  ❯ https://github.com/JUJING-DEEP/my-new-skill
```

**La documentación generada automáticamente incluye:**

- Título del proyecto + fila de badges (Stars / License / Version)
- Descripción de una línea
- Características principales (3-5 puntos detallados)
- Inicio rápido (en 5 minutos)
- Instrucciones de uso detalladas
- Tabla de configuración
- Al menos 3 ejemplos de uso
- Árbol de estructura del proyecto
- Guía de contribuciones
- Licencia MIT

---

## Cómo funciona

```
Creas un nuevo Skill
         ↓
El comando /publish activa
         ↓
┌──────────────────────────────────────┐
│       GitHub Publisher Skill          │
│  1. Lee el código del Skill           │
│  2. Invoca la lógica de generación   │
│  3. Pulido al estilo de proyectos     │
│     de alta calificación              │
│  4. Escribe README.md                │
│  5. git add / commit / push          │
└──────────────────────────────────────┘
         ↓
Repositorio GitHub (documentación completa y profesional)
```

### Phase 1: Recopilación de información

1. Confirmar la ruta del Skill objetivo
2. Leer los siguientes archivos:
   - `SKILL.md` o archivo de lógica principal
   - Todos los archivos bajo `references/`
   - Todos los archivos bajo `scripts/`
   - `README.md` existente (si lo hay)
3. Extraer información clave:
   - Nombre del Skill y funcionalidad principal
   - Formato de entrada/salida
   - Dependencias y compatibilidad
   - Casos de uso y condiciones de activación

### Phase 2: Generar README

Secciones requeridas (en orden):

1. **Título del proyecto + Badges**
2. **Descripción de una línea**
3. **Placeholder de GIF/Screenshot de demo**
4. **Características principales** (3-5 puntos)
5. **Inicio rápido**
6. **Instrucciones de uso detalladas**
7. **Configuración** (formato tabular)
8. **Ejemplos de uso** (al menos 3)
9. **Estructura del proyecto**
10. **Guía de contribuciones**
11. **Licencia**

### Phase 3: Control de calidad

- [ ] Todos los bloques de código tienen etiqueta de lenguaje
- [ ] Los pasos de instalación se pueden seguir
- [ ] Sin "TODO" o placeholders vacíos
- [ ] Cada fila de la tabla de configuración tiene valor por defecto

### Phase 4: Publicación Git

```bash
cd <skill-path>
git add README.md
git commit -m "docs: auto-generate README"
git push origin main
```

---

## Instalación

GitHub Publisher está basado en el protocolo abierto [Agent Skills](https://agentskills.io) y puede ejecutarse en cualquier runtime de agente AI compatible con skills.

### Método 1: Un comando (Recomendado, multiplataforma)

Abre el agente que estés usando (Claude Code, Codex, Cursor, OpenClaw, Hermes, CodeBuddy, Workbuddy, Gemini CLI, OpenCode, etc.) y dile:

```
Instala este skill: https://github.com/JUJING-DEEP/github-publisher
```

O usa el instalador CLI universal ([vercel-labs/skills](https://github.com/vercel-labs/skills), compatible con 55+ runtimes):

```bash
npx skills add JUJING-DEEP/github-publisher
```

### Método 2: Instalación manual

<details>
<summary>Ver directorios de skills para cada runtime</summary>

| Runtime | Ruta de instalación |
|---|---|
| Claude Code | `~/.claude/skills/github-publisher/` |
| Codex CLI | `~/.codex/skills/github-publisher/` |
| Cursor | `~/.cursor/skills/github-publisher/` |
| OpenClaw | `~/.openclaw/workspace/skills/github-publisher/` |
| Hermes Agent | Ejecutar `tools/install_hermes_skill.py` |
| Otros runtimes | Clonar al directorio `skills/` del runtime correspondiente |

```bash
git clone https://github.com/JUJING-DEEP/github-publisher <ruta de la tabla anterior>
```

</details>

---

## Uso

### Comando básico

```
/publish
```

### Con ruta específica

```
/publish skills/my-new-skill
```

### Activar desde otros agentes

```
Publica este Skill en GitHub: skills/my-data-analyzer
```

---

## Plataformas soportadas

| Plataforma | Estado | Comando de instalación |
|------|------|---------|
| Claude Code | ✅ Soporte completo | `/skill add JUJING-DEEP/github-publisher` |
| Codex | ✅ Soporte completo | `npx skills add JUJING-DEEP/github-publisher` |
| Cursor | ✅ Soporte completo | `npx skills add JUJING-DEEP/github-publisher` |
| OpenClaw | ✅ Soporte completo | `npx skills add JUJING-DEEP/github-publisher` |
| Hermes Agent | ✅ Soporte completo | Consultar instalación manual |
| Otras plataformas | ✅ Compatible | Consultar [Protocolo Agent Skills](https://agentskills.io) |

---

## Estructura del proyecto

```
github-publisher/
├── SKILL.md                         # Lógica principal del Skill
├── README.md                        # Este archivo (chino)
├── README_EN.md                     # Versión en inglés
├── README_JA.md                    # Versión en japonés
├── README_KO.md                    # Versión en coreano
├── README_ES.md                     # Este archivo
├── LICENSE                          # Licencia MIT
├── assets/
│   └── demo.gif                     # Animación de demo
├── references/
│   ├── readme-template.md           # Plantilla README de alta calificación
│   └── style-guide.md               # Guía de estilo de redacción
└── .claude/
    └── commands/
        └── publish.md              # Definición del comando /publish
```

---

## Notas

1. **Si el Skill ya tiene README**: Comparar diferencias, actualizar solo partes faltantes
2. **Si git push falla**: Verificar configuración de remote y permisos del Token
3. **Tono del documento generado**: Profesional pero no robótico
4. **Lista negra de fuentes**: No incluye Zhihu, cuentas de WeChat público, etc.

---

## Sobre el autor

**巨鲸r** — AI Native Developer · Mismo nombre en todas las plataformas

| Plataforma | Enlace |
|------|------|
| 🐧 WeChat | **巨鲸r** (Buscar en WeChat) |
| 𝕏 Twitter | [@JUJING_DEEP](https://x.com/JUJING_DEEP) |
| GitHub | [JUJING-DEEP](https://github.com/JUJING-DEEP) |

> El código QR está en assets/wechat-qrcode.jpg ↓

## Licencia

MIT — Úsalo libremente, modifícalo libremente, distribúyelo libremente.

---

<div align="center">

MIT License © [JUJING-DEEP](https://github.com/JUJING-DEEP)

</div>
