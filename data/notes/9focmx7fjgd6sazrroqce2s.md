
## xterm 踩雷經驗
### 在使用 xterm 的時候，遇到一些問題，這邊做一些紀錄

- **當使用 attachCustomKeyEventHandler 時，_絕對_ 要 return true/false**


  會註冊成 `_customKeyEventHandler`，並在 `_keyDown, _keyUp, _keyPress` 中被呼叫，  
  並以 `if (this._customKeyEventHandler(ev))` 來判斷是否要繼續處理 key event

[CodeLink](https://github.com/xtermjs/xterm.js/blob/6e351dd4ac23235c587dbf4af4cac737965cb7cd/src/browser/Terminal.ts#L1102)

```typescript
protected _keyPress(ev: KeyboardEvent): boolean {
    let key;

    this._keyPressHandled = false;

    if (this._keyDownHandled) {
      return false;
    }

    if (this._customKeyEventHandler && this._customKeyEventHandler(ev) === false) {
      return false;
    }
...
}
```

  如果沒有 return true/false，會導致 key event 會被繼續傳遞，而且會將原生事件 cancel，  
  導致其他的 xterm key event handler (_keyDown, _keyUp, _keyPress, ...) 也會被觸發


- 有自己的 cancel function 會在某些地方被呼叫，導致 key event 被 cancel

[CodeLink](https://github.com/xtermjs/xterm.js/blob/6e351dd4ac23235c587dbf4af4cac737965cb7cd/src/browser/Terminal.ts#L1306)

```typescript
  // TODO: Remove cancel function and cancelEvents option
  public cancel(ev: Event, force?: boolean): boolean | undefined {
    if (!this.options.cancelEvents && !force) {
      return;
    }
    ev.preventDefault();
    ev.stopPropagation();
    return false;
  }
}
```


