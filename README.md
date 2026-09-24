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

## License

MIT License

Copyright (c) 2026 userAnonymous

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE
SOFTWARE.
