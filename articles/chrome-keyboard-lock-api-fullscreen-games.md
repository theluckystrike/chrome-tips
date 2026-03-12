---
layout: "post"
title: "Chrome Keyboard Lock API: Building Immersive Fullscreen Games"
description: "Learn how to use the Chrome Keyboard Lock API to capture keyboard input for immersive fullscreen web games. Step-by-step guide with code examples. Check out ou"
date: "2026-01-15"
last_modified_at: "2026-03-11"
permalink: "chrome-keyboard-lock-api-fullscreen-games"
categories: [chrome, web-development, gaming, api, javascript]
tags: [keyboard-lock-api, fullscreen-games, chrome-api, web-gaming, browser-gaming, game-development]
author: "theluckystrike"
---
# Chrome Keyboard Lock API: Building Immersive Fullscreen Games

When building web-based games that require fullscreen immersion, one of the most frustrating issues developers face is unexpected browser keyboard shortcuts interrupting gameplay. Pressing Alt+Tab to switch windows, Ctrl+W to close tabs, or Escape to exit fullscreen can instantly break the gaming experience. This is where the Chrome Keyboard Lock API comes in—a powerful feature that allows web applications to capture keyboard input exclusively for immersive fullscreen experiences.

## What Is the Keyboard Lock API?

The Keyboard Lock API, part of the Keyboard API specification, enables a web page to request capture of keyboard keys that are normally handled by the browser or operating system. When activated, keys like Escape, Alt+Tab, Ctrl+W, and other system shortcuts are redirected to the web application instead of triggering their default browser behaviors.

This API is particularly valuable for:

- Browser-based games requiring precise keyboard control
- Virtual desktop environments running in Chrome
- Interactive presentations and demos
- Fullscreen web applications that need uninterrupted keyboard focus

## Browser Compatibility

Before diving into implementation, it's important to note that the Keyboard Lock API has limited browser support. It works in Chrome, Edge, and other Chromium-based browsers, but Firefox and Safari have not yet implemented this feature. For a truly accessible game, you'll need to provide fallback messaging or alternative controls for users on unsupported browsers.

## How to Request Keyboard Lock

The API is straightforward to use. The core method is `navigator.keyboard.lock()`, which requests that all keyboard events be dispatched to the locked element (typically the document). Here's the basic implementation:

```javascript
async function lockKeyboard() {
  try {
    await navigator.keyboard.lock();
    console.log('Keyboard locked successfully');
  } catch (error) {
    console.error('Failed to lock keyboard:', error);
  }
}
```

The `keyboard.lock()` method accepts an optional array of specific key codes to lock. If no array is provided, all keys are locked:

```javascript
// Lock all keys
await navigator.keyboard.lock();

// Lock only specific keys (Escape in this case)
await navigator.keyboard.lock(['Escape']);
```

## Fullscreen Integration

The Keyboard Lock API works most reliably when combined with the Fullscreen API. Most browsers require a user gesture (like a click) before activating either fullscreen or keyboard lock. Here's how to implement both together:

```javascript
async function startGame() {
  try {
    // Request fullscreen first
    await document.documentElement.requestFullscreen();
    
    // Then lock the keyboard
    await navigator.keyboard.lock();
    
    console.log('Game mode activated - fullscreen and keyboard locked');
  } catch (error) {
    console.error('Failed to start game mode:', error);
  }
}

// Attach to a start button
document.getElementById('startButton').addEventListener('click', startGame);
```

## Handling the Escape Key

One of the most common use cases for keyboard lock is capturing the Escape key in games. Normally, pressing Escape in fullscreen mode exits fullscreen immediately. With keyboard lock, you can intercept this key for game purposes:

```javascript
document.addEventListener('keydown', (event) => {
  if (event.code === 'Escape') {
    // Handle escape for game menu instead of exiting fullscreen
    event.preventDefault();
    toggleGameMenu();
  }
});

document.addEventListener('keyup', (event) => {
  if (event.code === 'Escape') {
    event.preventDefault();
    console.log('Escape key released');
  }
});
```

## Practical Example: Building a Fullscreen Game Controller

Let's put together a practical example that demonstrates a fullscreen game with keyboard control:

```javascript
class GameController {
  constructor() {
    this.keysPressed = new Set();
    this.setupKeyboardListeners();
  }

  setupKeyboardListeners() {
    document.addEventListener('keydown', (event) => {
      this.keysPressed.add(event.code);
      
      // Handle game-specific shortcuts
      switch (event.code) {
        case 'KeyW':
        case 'ArrowUp':
          this.handleMove('forward');
          break;
        case 'KeyS':
        case 'ArrowDown':
          this.handleMove('backward');
          break;
        case 'KeyA':
        case 'ArrowLeft':
          this.handleMove('left');
          break;
        case 'KeyD':
        case 'ArrowRight':
          this.handleMove('right');
          break;
        case 'Space':
          this.handleAction('jump');
          break;
      }
    });

    document.addEventListener('keyup', (event) => {
      this.keysPressed.delete(event.code);
    });
  }

  handleMove(direction) {
    console.log(`Moving ${direction}`);
    // Add your movement logic here
  }

  handleAction(action) {
    console.log(`Action: ${action}`);
    // Add your action logic here
  }

  isKeyPressed(keyCode) {
    return this.keysPressed.has(keyCode);
  }

  async activate() {
    await document.documentElement.requestFullscreen();
    await navigator.keyboard.lock();
  }

  async deactivate() {
    if (document.fullscreenElement) {
      await document.exitFullscreen();
    }
    navigator.keyboard.unlock();
  }
}
```

## Unlocking the Keyboard

When your game ends or the user needs to exit, always properly unlock the keyboard:

```javascript
// Unlock keyboard - returns control to the browser
navigator.keyboard.unlock();

// Exit fullscreen as well
if (document.fullscreenElement) {
  await document.exitFullscreen();
}
```

It's good practice to unlock the keyboard when the user presses Escape multiple times quickly, or when they explicitly want to exit your game interface.

## Best Practices for Implementation

When implementing keyboard lock in your games, consider these best practices:

1. **Always require user interaction**: The keyboard lock request must be triggered by a user action like a click or button press. Silent or automatic locking will fail.

2. **Provide clear exit instructions**: Make sure users know how to exit your game. Consider adding an on-screen hint showing how to return control to the browser.

3. **Handle browser restrictions gracefully**: Some browsers may deny keyboard lock requests, especially if not in fullscreen mode. Always wrap your calls in try-catch blocks.

4. **Unlock on page unload**: Add an event listener for `beforeunload` to ensure the keyboard is unlocked if the user refreshes or closes the tab.

5. **Test across devices**: Keyboard lock behavior can vary between operating systems and Chrome versions. Test thoroughly on your target platforms.

## Performance Considerations

The Keyboard Lock API itself has minimal performance impact since it simply redirects events. However, when handling rapid keyboard input in games, consider these optimization tips:

- Use `requestAnimationFrame` for game loops instead of `setInterval`
- Debounce rapid key events if your game doesn't need per-key-frame updates
- Consider using `event.code` instead of `event.key` for consistent physical key identification

## Conclusion

The Chrome Keyboard Lock API opens up exciting possibilities for building immersive fullscreen web games and applications. By capturing keyboard input that would otherwise be intercepted by the browser, you can create gaming experiences that feel as responsive as native applications.

While browser support remains limited to Chromium-based browsers, this API is a valuable tool for game developers targeting Chrome users. Combined with the Fullscreen API and proper user experience considerations, keyboard lock helps deliver the focused, immersive experiences that players expect from modern web games.

For developers building browser-based games, pairing keyboard lock with extensions like Tab Suspender Pro can help maintain optimal performance by managing background tabs while players enjoy uninterrupted gameplay.

Built by theluckystrike — More tips at [zovo.one](https://zovo.one)

## Related Articles

- [Chrome Extensions for Social Media Managers](/articles/chrome-extensions-for-social-media-managers)
- [Chrome Wappalyzer Alternative Built In](/articles/chrome-wappalyzer-alternative-built-in)
- [Chrome Extension Alternative to Grammarly Free](/articles/chrome-extension-alternative-to-grammarly-free)
