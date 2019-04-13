# Demandware with ease

### This repository contains only the localization files for the extension. Any contributions to the translations are always welcome and gladly appreciated!

---
### Use Salesforce Commerce Cloud B2C with ease!
---
### An extension which makes Salesforce Commerce Cloud B2C a happy place!
---
### This plugin is intended for developer sandboxes and should be used with caution for staging and production sandboxes!
---
## List of functionalities

## Options Page
#### Store your sandboxes
    You can store all of your sandbox instances, and use individual options for each of them.

    Open sandbox - will open the selected sandbox Business Manager Home page.
    Copy sandbox - will create a new instance with the same credentials as the selected sandbox.
    Edit sandbox - will allow you to edit your information any time.
    Remove sandbox

    Keep BM Session Alive - will make your session never expire after
    the 15 minutes period in Business Manager.

    Login in BM automatically - will automatically log-in Business Manager
    whenever the login screen pops up,if username and password is present.

#### Secured Password
    Your passwords are stored securely using AES
    encryption and are never visible in plain text once input.
    Note: Passwords are optional.However, keep in mind
    that you will not be able to use the automatic login functionallity.

#### Sandbox Options
    Notifications - turn on/off notifications.
    Scroll log to bottom - scrolls you to the bottom of the page when you are inside .log file
    Trim logs (X) - turn on/off trim of files lines inside .log file
    Beautify logs (none,colorize,beautify) - formats the logs for better readability
    Automatically login in XChange - turn on/off, will auto login if credentials are present
    Keep XChange session alive - makes the XChange session never expire

#### Select Default Site
    Specifies a site to be selected upon log-in, to disable this function, leave blank

#### Import / Export
    Import & Export your sandbox configurations in JSON config file.Passwords are not exported.

## Menu Page
#### Context menu
    Where you can rearange the context menu positions with drag and drop, or add new pages to it.
    You can set which one you want to be active and appear, and leave the unused for now as inactive.
    The context menu can be accessed by right clicking inside a saved sandbox browser tab.

## Business Manager Context

#### Account Lock Protection
    The extension stops auto login process immediately after wrong password,
    which protects your account from getting locked.Re-check your credentials and try again.

#### Apply/Update Hotkey
    You can use CTRL + S hotkey to instantly click the update/apply button,
    on Product edit and Content asset edit pages and save your changes.

#### Recreated buttons on development
    Recreated New and Delete buttons in System Object - > Attribute Definitions.
    Recreated New Attribute Group form and Delete button in System Object - > Attribute Grouping.

## Extension Popup
#### Smart Shortcuts
    Gain faster access to most popular pages or quickly edit your sandbox.

## WebDav Pages
#### Enhanced logs
    Today and yesterday logs are reordered on top of the logs page and are highlighted.
    If this option is enabled it also highlights most important words on logs.

#### Breadcrumbs
    Transformed breadcrumb in webvdav to be clickable for easier navigation

#### File Actions
    When you are in one of the following places in webdav - /Cartridges, /Impex, /Securitylogs, /Temp, /Static, /Library
    The following options are present:
    - Upload file area, where you can drop files to upload them all, or left click to upload single file.
    - Create new folder button
    - Delete folder/file
    - Empty file
    - Edit file

## Sandbox Context
#### Download content asset button
    The extension adds an additional button inside the edit content asset page,
    where you can download xml export of the current asset and all of its populated attributes.

#### Notifications
    The extension will notify you if you visit a demandware sandbox which is not saved or,
    if the password input is wrong.You can turn off notifications in the options menu.

#### Helper Context Menu
    Right-click context menu, to gain faster access to most popular pages.
    The menu consists of 5 default pages, and you can add any custom page from the options page menu page.
