<h1>
  <img src="_assets/logo.png" alt="DWE logo" height="40" align="left" />
  Demandware with Ease
</h1>

> Use Salesforce Commerce Cloud B2C with ease!

## 📦 Install

- [DWithEase for Chrome](https://chrome.google.com/webstore/detail/demandware-with-ease/ffhabonelknmejmdnekedmijlhebpcio)
- [DWithEase for Firefox](https://addons.mozilla.org/en-US/firefox/addon/dwithease/)
- [DWithEase for Microsoft Edge](https://microsoftedge.microsoft.com/addons/detail/peefidlcfhcdelglpfhfbmniafbocgag)

## 📖 About This Repo

This is the official public repository for **Demandware with Ease**. It contains the localization files for the extension. Contributions to the translations are always welcome and gladly appreciated.

## ⚠️ Recommended Usage

This extension is intended for **developer sandboxes**. Use with caution on staging and production sandboxes.

## 🤝 Community Contributions

DWE includes a **custom plugin system** that lets anyone write their own JavaScript or CSS and run it on Business Manager pages. Plugins are managed from the Plugins tab in the extension options, route-gated per page, and exported as portable `.dweplugin` files for sharing.

If you have built a plugin that other developers would benefit from, submit it for inclusion natively in the extension:

Accepted plugins are bundled into the next release and credited to the author on the extension's About page.

See **[plugins/contribution.md](plugins/contribution.md)** for the full submission guide — file format, route-gating modes, authoring guidelines, security expectations, size limits, and review criteria.


## ✨ List of Functionalities

### ⚙️ Options Page

#### 🗄️ Store Your Sandboxes

Store all of your sandbox instances and use individual options for each of them.

- **Open sandbox** — opens the selected sandbox Business Manager home page.
- **Copy sandbox** — creates a new instance with the same credentials as the selected sandbox.
- **Edit sandbox** — edit your information any time.
- **Remove sandbox** — delete a stored instance.
- **Keep BM Session Alive** — your session never expires after the 15-minute period in Business Manager.
- **Login in BM automatically** — auto-logs into Business Manager whenever the login screen appears, if username and password are present.

#### 🔒 Secured Password

Passwords are stored securely using AES encryption and are never visible in plain text once entered.

> **Note:** passwords are optional. Without one, the automatic login functionality is unavailable.

#### 🎛️ Sandbox Options

- **Notifications** — turn notifications on/off.
- **Scroll log to bottom** — scrolls to the bottom of the page when viewing a `.log` file.
- **Trim logs (X)** — turn on/off line trimming inside `.log` files.
- **Beautify logs** (`none`, `colorize`, `beautify`) — formats logs for better readability.
- **Automatically login in XChange** — auto-logs in if credentials are present.
- **Keep XChange session alive** — makes the XChange session never expire.

#### 🔄 Import / Export

Import and export your sandbox configurations as a JSON config file so you do not lose your settings. **Passwords are not exported.**

### 📋 Menu Page

#### 🖱️ Context Menu

Rearrange context-menu positions via drag and drop, or add new pages. Set which entries are active and leave unused ones inactive. The context menu is accessed by right-clicking inside a saved sandbox browser tab.

### 💼 Business Manager Context

#### 🛡️ Account Lock Protection

The extension stops the auto-login process immediately after a wrong password, protecting your account from being locked. Re-check your credentials and try again.

#### ⌨️ Apply/Update Hotkey

Use `CTRL + S` to instantly click the Update / Apply button on Product Edit and Content Asset Edit pages and save your changes.

#### 🔘 Recreated Buttons on Development

- Recreated **New** and **Delete** buttons in *System Object → Attribute Definitions*.
- Recreated **New Attribute Group** form and **Delete** button in *System Object → Attribute Grouping*.

### 💬 Extension Popup

#### ⚡ Smart Shortcuts

Quick access to:

- Your sandboxes list (Open BM or Edit Configuration)
- Configured context menu per configuration
- Link to extension options page
- Link to SFCC Documentation / XChange

### 🌐 WebDav Pages

#### 📜 Enhanced Logs

Today's and yesterday's logs are reordered to the top of the logs page and highlighted. When enabled, the most important words in logs are also highlighted.

#### 🍞 Breadcrumbs

The breadcrumb in WebDav is transformed into clickable segments for easier navigation.

#### 📁 File Actions

In `/Cartridges`, `/Impex`, `/Securitylogs`, `/Temp`, `/Static`, and `/Library`:

- **Upload file area** — drop files to upload all of them, or left-click to upload a single file.
- **Create new folder** button
- **Delete folder/file**
- **Empty file**
- **Edit file**

### 🏖️ Sandbox Context

#### ⬇️ Download Content Asset Button

Adds an extra button inside the Edit Content Asset page that downloads an XML export of the current asset and all of its populated attributes.

#### 🔔 Notifications

The extension notifies you when you visit a Demandware sandbox that is not saved, or when the password input is wrong. Notifications can be disabled in the options menu.

#### 🆘 Helper Context Menu

A right-click context menu for faster access to popular pages. Five default pages, plus any custom pages added from the options Menu page.

---
