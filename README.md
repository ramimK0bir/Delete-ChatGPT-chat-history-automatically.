# ChatGPT Chat Deleter

A small browser-console JavaScript snippet that repeatedly deletes ChatGPT conversations through the visible UI.

> **Note:** This is an unofficial automation script. It relies on ChatGPT's current DOM selectors, which may change at any time. Use it only on your own account and review the script before running it.

## Script

```javascript
function delete_chat(){
    a = document.querySelector('#history [class="list-none"] [aria-label]')
    b = document.querySelector('[aria-label="More"]')
    c = document.querySelector('[role="menuitem"][data-color="danger"]')
    d = document.querySelector('[data-testid="delete-conversation-confirm-button"]')
    delay = 0

    if (!b && !c && !d) {
        delay = 300
        a?.click()
    }
    else if (!c && !d) {
        delay = 500
        b?.click()
    }
    else if (!d) {
        delay = 700
        c?.click()
    }
    else {
        delay = 2500
        d?.click()
    }

    setTimeout(delete_chat, delay)
}

delete_chat()
```

## How it works

The function repeatedly checks for four UI elements:

1. A conversation in the chat history.
2. The **More** menu.
3. The delete menu item.
4. The delete confirmation button.

It clicks whichever step is currently available, waits briefly, and then runs again.

## Usage

1. Open ChatGPT in your browser.
2. Open the browser developer console.
3. Paste the script.
4. Run it.
5. Stop execution if necessary using the browser's developer tools.

## Important

This script can delete conversations **irreversibly**. Make sure you actually want to remove the chats before running it.

The DOM selectors are implementation details of the web interface and can break when the interface changes.
