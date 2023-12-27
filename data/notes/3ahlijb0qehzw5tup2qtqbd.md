
 ## [2754. Bind Function to Context](https://leetcode.com/problems/bind-function-to-context/)

```javascript
/**
 * @param {Object} obj
 * @return {Function}
 */
Function.prototype.bindPolyfill = function(obj) {
  let fn = this;
  return function (...args) {
    return fn.call(obj, ...args); // OR return fn.apply(obj, args);
  }
}

```

思路：
在不能用 bind 的情況下，將 `obj` 帶入 thisArgs 為這 function 可以讀到的 this scope

## [2632.Curry](https://leetcode.com/problems/curry/)

原理：
將函數的參數傳遞方式彈性運用，像是

```javascript
function sum(a, b, c) {  
  return a + b + c;
}
let curriedSum = curry(sum);
alert( curriedSum(1, 2, 3) ); // 6，仍然可以被正常调用
alert( curriedSum(1)(2,3) ); // 6，对第一个参数的柯里化
alert( curriedSum(1)(2)(3) ); // 6，全柯里化
```

思路：
1. 運用兩層 function
2. 確認原本 function 的參數長度，如果傳進來的參數長度大於原本的長度，將參數合併重新傳遞給上層 function

```javascript
var curry = function(fn) {
  return function curried(...args) {
    if (args.length >= fn.length) {
      return fn(...args);
    } else {
      return function(...args2) {
        return curried(...args, ...args2);
      };
    }
  };
};
```

## [2627. Debounce](https://leetcode.com/problems/debounce/)
Given a function fn and a time in milliseconds t, return a **debounced** version of that function.

![](/assets/debounce.png)

A **debounced** function is a function whose execution is delayed by t milliseconds and whose execution is cancelled if it is called again within that window of time. The debounced function should also receive the passed parameters.

思路：
在原本的 setTimeout 被設定後，新的 TimeoutId 會把原本的 TImeoutId 給清除，同樣會給定時間後執行

```javascript
/**
 * @param {Function} fn
 * @param {number} t milliseconds
 * @return {Function}
 */
var debounce = function(fn, t) {
  let timeoutId;
  return function(...args) {
	if (timeoutId) {
 	  clearTimeout(timeoutId);
   }
   
   timeoutId = setTimeout(() => fn(...args), t); //notice: must execute fn()
}
```

## [2676. Throttle](https://leetcode.com/problems/throttle/)

Given a function fn and a time in milliseconds t, return a **throttled** version of that function.
A **throttled** function is first called without delay and then, for a time interval of t milliseconds, can't be executed but should store the latest function arguments provided to call fn with them after the end of the delay.

![](/assets/throttle.png)

思路：
1. 利用 storedArg 確認 timeoutFunc 是否還需要做遞迴執行, waiting 確認 fn 執行後，再次被呼叫後，是否需要等待
2. timeoutFunc 用來執行被延遲的 func，如果在 waiting，會等到 waiting 結束後從 storedArg 執行，但如果執行 waiting 後的 func ，又有新的不同 func 進來，確保有被執行到 


```javascript
function throttle(fn, t) {
    let storedArg = null;
    let waiting = false;

	// step 2.
    function timeoutFunc() {
        if (!storedArg) {
            waiting = false;
            return;
        }

        fn(...storedArg);
        storedArg = null;
        setTimeout(timeoutFunc, t);
    }

	// step 1.
    return function(...args) {
        if (waiting) {
            storedArg = args;
            return;
        }

        fn(...args);
        waiting = true;
        setTimeout(timeoutFunc, t);
    }
}


```

## [2628. JSON Deep Equal](https://leetcode.com/problems/json-deep-equal/description/)

思路：
1. 檢查是否相等
2. 如果是其中一個是 null，及早 return false
3. 利用 String() 判斷, 特例：
   `String({"0":1}) String([1]) => [object object] 1` 
4. 判斷是否為 Array ，再來判斷長度，一樣用遞迴判斷內容是否相等
5. 判斷是否為 Object，再來判斷 property 長度，一樣用遞迴判斷內容是否相等
6. 最後 return true

``` javascript
/**
 * @param {any} o1
 * @param {any} o2
 * @return {boolean}
 */
var areDeeplyEqual = function(o1, o2) {
  if (o1 === o2) return true;
  if (o1 === null || o2 === null) return false;
  if (String(o1) !== String(o2)) return false;

  if (typeof o1 !== 'object') {
    if ( o1 !== o2) {
      return false;
    }
  }

  if (Array.isArray(o1)) {
    if (o1.length !== o2.length) {
      return false;
    }

    for (let i = 0; i < o1.length; i++) {
      if (!areDeeplyEqual(o1[i], o2[i])) {
        return false;
      }
    }
  }

  if (typeof o1 === 'object' && o1 !== null) {
    const keys1 = Object.keys(o1);
    const keys2 = Object.keys(o2);

    // Check if they have the same number of keys
    if (keys1.length !== keys2.length) {
        return false;
    }

    for (let key in o1) {
      if (!areDeeplyEqual(o1[key], o2[key])) {
        return false;
      }
    }
  }

  return true;
};

```
## [2636. Promise Pool](https://leetcode.com/problems/promise-pool/description/)

思路：
因為 functions 不能用 iteration 的方式，所以用遞迴的方式，每次都把 functions 的第一個 function 執行，並且把剩下的 functions 傳遞給下一次的遞迴

1. 寫出 helper 目的讓 array 用 shift 出第一個 function，並且把剩下的 functions 傳遞給下一次的 helper 遞迴
2. 將 functions 轉成長度為 function 長度的 array 重複執行 helper
3. return new Promise.all 結果

```javascript
type F = () => Promise<any>;

function promisePool(functions: F[], n: number): Promise<any> {
  async function evaluateFunction(): Promise<any> {
    if (functions.length > 0) {
      let f = functions.shift();
      if (f) {
        await f();
        await evaluateFunction();
      }
    }

    return;
  }

  let promises = Array(n).fill(0).map(() => evaluateFunction());
  return Promise.all(promises);
};
```


## [2625. Flatten Deeply Nested Array](https://leetcode.com/problems/flatten-deeply-nested-array/description/)

思路：
1. 輪詢 array
2. 利用遞迴，如果是 array 就繼續遞迴，如果不是就 push 到 result
3. n 層解構，每呼叫一自己，n 就減一，直到 n 為 0，就不再遞迴
4. 如果不是 array 就 push 到 result

```javascript
type MultiDimensionalArray = (number | MultiDimensionalArray)[];

var flat = function (arr: MultiDimensionalArray, n: number): MultiDimensionalArray {
	let res: MultiDimensionalArray = [];

	for(let i = 0; i < arr.length; i++) {
    if (Array.isArray(arr[i]) && n > 0) {
      res.push(...flat(arr[i] as MultiDimensionalArray, n -1));
    } else {
      res.push(arr[i]);
    }
  }
    
	return res;
};
```

#leetcode #javascript