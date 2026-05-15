# Contributing a DWE Plugin

Demandware with Ease (DWE) includes a custom user-script system that lets anyone write their own JavaScript or CSS and run it on Salesforce B2C Commerce Business Manager pages — no fork, no rebuild, no extension reload. If you have built a plugin that you think other developers would benefit from, this guide explains how to submit it for inclusion natively in the extension.

## Table of Contents

- [What is a DWE Plugin?](#what-is-a-dwe-plugin)
- [Before You Submit](#before-you-submit)
- [Submission Workflow](#submission-workflow)
- [Plugin File Format](#plugin-file-format)
- [Where Plugins Run](#where-plugins-run)
- [Route Gating (`shouldRun`)](#route-gating-shouldrun)
- [Authoring Guidelines](#authoring-guidelines)
- [Security Expectations](#security-expectations)
- [Size Limits](#size-limits)
- [Review Criteria](#review-criteria)
- [Credit](#credit)

## What is a DWE Plugin?

A DWE Plugin is a single block of JavaScript **or** CSS that the extension injects into a Business Manager page. Plugins are managed from the **Plugins** tab on the options page, written in the bundled ACE editor, and toggled on or off per-plugin. They sync across browsers via `chrome.storage.sync` and can be exported as portable `.dweplugin` files for sharing.

In short: a plugin is a sharable bookmarklet with a UI, route gating, and cross-browser sync.

## Before You Submit

- Check if the feature does not already exist in the extension.
- Ensure the plugin is **safe for production**, or it gates itself to development hosts. Anything that mutates BM data without an explicit user click will be rejected.
- The plugin works against the all supported Business Manager styles and versions.
- You have tested it from a clean profile - no stale state, no other extensions interfering.

## Submission Workflow

1. **Open an issue** describing the plugin: what it does, which BM pages it targets, and why other developers would want it.
2. **Fork** this repository.
3. **Export your plugin** from the DWE options page (`Export` action on the row) — this produces a `.dweplugin` file.
4. **Add the file** under `plugins/<your-plugin-name>/` along with a short `README.md` and any screenshots or GIFs.
5. **Open a pull request** linking the issue.
6. Respond to review feedback. Approved plugins are bundled into the next extension release.

## Plugin File Format

A `.dweplugin` file is a JSON array of plugin objects (always an array, even for a single plugin). Each object has this shape:

```json
{
  "name": "Your Plugin Name",
  "description": "One sentence describing what the plugin does.",
  "type": "js",
  "enabled": true,
  "shouldRunMode": "regex",
  "shouldRunValue": "ViewProduct_.*",
  "shouldRunFlags": "i",
  "content": "(function(){ /* your code */ })();"
}
```

Field reference:

| Field | Values | Purpose |
| --- | --- | --- |
| `name` | string | Display name in the BM dropdown and options table |
| `description` | string | Free text shown in the table column and as hover tooltip |
| `type` | `"js"` or `"css"` | Editor mode and how content is injected |
| `enabled` | boolean | Default state on import (recommend `false` for unverified plugins) |
| `shouldRunMode` | `"all"`, `"regex"`, `"function"` | How `shouldRun` is evaluated |
| `shouldRunValue` | string | Regex pattern or function body, depending on mode |
| `shouldRunFlags` | string | Regex flags (only used when `shouldRunMode` is `"regex"`) |
| `content` | string | The JS or CSS source |

`id`, `createdAt`, and `updatedAt` are stripped on export and regenerated on import.

## Where Plugins Run

Plugins execute in the **page's MAIN world**, injected by the background service worker through `chrome.scripting.executeScript`. This means:

- Full access to the Business Manager page DOM, cookies, and JS globals (jQuery, Angular, etc.).
- No access to extension APIs (`chrome.*`) — plugins are sandboxed away from the extension itself.
- CSS plugins are injected as a `<style data-dwe-plugin="...">` tag in `<head>`.
- JS plugins are wrapped in an IIFE with `try/catch`. Errors produce a `console.error` and a native `alert("Plugin \"X\" error: ...")` so the user sees what broke.

Toggling a plugin on or off persists immediately but **requires a page reload** to take effect. The BM dropdown shows a pulsing reload button when a reload is pending.

## Route Gating (`shouldRun`)

Each plugin decides per page-load whether to execute. Three modes:

**`all`** — run on every BM page the extension is active on. Use sparingly.

**`regex`** — match `location.href` against a regex pattern.
```json
{
  "shouldRunMode": "regex",
  "shouldRunValue": "ViewProduct_.*|ViewContentAsset_.*",
  "shouldRunFlags": "i"
}
```

**`function`** — supply a JS body that returns a boolean. Receives no arguments; has access to `location`, `document`, `window`.
```json
{
  "shouldRunMode": "function",
  "shouldRunValue": "return location.pathname.includes('/on/demandware.store/') && document.querySelector('#editproduct_form');"
}
```

> Prefer the most specific mode that works. `all` plugins are reviewed more strictly.

## Authoring Guidelines

- **Vanilla preferred.** - Use plain JavaScript and CSS.
- **No credential reads.** Do not touch password fields, cookies tied to auth, or anything that could exfiltrate session state.
- **No console noise** in steady state. Log errors, not every action.
- **Idempotent.** A plugin must tolerate being injected once per page-load and must not break on re-injection during SPA-style navigation.

## Security Expectations

DWE plugins run with the same privileges as the user on the BM page — equivalent to pasting code into DevTools. The extension shows an explicit warning on import: *"Plugins run with full access to the page. Only use code you trust."*

For a plugin to be accepted into the native bundle, the bar is higher than that warning. Reviewers will reject plugins that:

- Send data to any host other than the current BM origin.
- Read or modify password / API-key fields.
- Override or wrap built-in BM functions in a way that could mask errors.
- Use `eval` or dynamic `new Function` on user-controlled strings.
- Hide their behavior (obfuscation, minification, base64-wrapped code).

Code must be human-readable and reviewable.

## Size Limits

`chrome.storage.sync` allows roughly **8KB per item**. After JSON encoding, a plugin must fit in **~7KB**. The editor warns at 6KB. If your plugin is larger, factor it down — most BM tweaks are well under 1KB.

## Review Criteria

| Criterion | What we look for |
| --- | --- |
| Usefulness | Solves a real, recurring BM pain point |
| Safety | No data mutation without explicit user action; no exfiltration |
| Specificity | Tight `shouldRun` — does not run on pages it does not target |
| Quality | Readable code, no console noise, no broken pages |
| Scope | Does one thing well; does not duplicate existing features |
| Size | Comfortably under the 7KB sync-storage limit |

If the plugin is a good fit, it is merged and shipped natively in the next release. Once native, the user-script copy becomes redundant and can be removed from the user's own plugin list.

## Credit

Accepted plugins are credited to the author's GitHub handle on the extension's About page and linked back to the original pull request. Thank you for making DWE better for everyone.
