
# Clousure 考題

clousure 考題：將 setTimeout 時間順序轉為循序執行，利用 clousure 包裝

```javascript
const timerA = (callback) => setTimeout(() => callback('a'), 500);
const timerB = (callback) => setTimeout(() => callback('b'), 200);
const timerC = (callback) => setTimeout(() => callback('c'), 300);

// let setTimeout callback executed sequentially
function promiseCall(func, callback) {
	return new Promise((resolve) => {
    func((v) => {
      callback(v);
      resolve();
    })
	});
}

doByOrder(console.log);
// should return a -> b -> c
async function doByOrder(callback) {
  // await promiseCall(timerA, callback);
  // await promiseCall(timerB, callback);
  // await promiseCall(timerC, callback);

  promiseIterable([
    {func: timerA, callback},
    {func: timerB, callback},
    {func: timerC, callback}
  ])
}

// doByOrder iterable

async function promiseIterable(callbackObject) {
  for (let item of callbackObject) {
    const { func, callback } = item
    await promiseCall(func, callback);
  }
}
```