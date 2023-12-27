
## Sliding Window

```javascript

var slidingWindow = function(s) {
    const window = new Map();
    
    let left = 0, right = 0;
    while (right < s.length) {
        let c = s[right];
        window.set(c, (window.get(c) || 0) + 1);
        // 增大窗口
        right++;
        // 进行窗口内数据的一系列更新
        ...

        /*** debug 输出的位置 ***/
        // 注意在最终的解法代码中不要 console.log
        // 因为 IO 操作很耗时，可能导致超时
        console.log("window: [" + left + ", " + right + ")");
        /********************/
        
        // 判断左侧窗口是否要收缩
        while (window needs shrink) {
            // d 是将移出窗口的字符
            let d = s[left];
            window.set(d, window.get(d) - 1);
            // 缩小窗口
            left++;
            // 进行窗口内数据的一系列更新
            ...
        }
    }
}
```


## sliding window 思路
1、什麼時候該擴大窗口？
2、什麼時候該縮小窗口？
3、什麼時候該更新答案？

## 題目
| **LeetCode**                                                 | **难度** |
|:------------------------------------------------------------:|:------:|
| \| [3. Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/) | Medium |
| \| [438. Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/) | Medium |
| \| [567. Permutation in String](https://leetcode.com/problems/permutation-in-string/) | Medium |
| \| [76. Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/) | Hard   |

## BST

```javascript
var BST = function(root, target) {
    if (root.val === target) {
        // 找到目标，做点什么
    }
    if (root.val < target) { 
        BST(root.right, target);
    }
    if (root.val > target) {
        BST(root.left, target);
    }
};

```

[Validate Binary Search Tree](https://leetcode.com/problems/validate-binary-search-tree/)

注意：
當到左子樹時，root 應當為所有左子樹最大值，所有右邊都比左大，方為合法  BST
當到右子樹時，root 應當為所有右子樹最小值，所有左邊都比右小，方為合法  BST

## Binary Tree 基本題

Quick sort 為 binary tree 的 preorder, merge sort 為 binary tree 的 postorder

Quick sort pattern, 
```javascript
function quickSort(nums, lo = 0, hi = nums.length - 1) {
	if (lo < hi) {
		p = partition(nums, lo, hi);
		quickSort(nums, lo, p);
		quickSort(nums, p + 1, hi);
	}
}
```

```javascript
function partition(nums, lo, hi) {
	let piviot = nums[hi];
	let i = lo;
	for (let j = lo; j < hi; i++) {
		if (nums[lo] < piviot) {
			[nums[lo], nums[hi]] = [nums[hi], nums[lo]];
		}
		i++
	}

	[nums[i], piviot] = [piviot, nums[i]];
	return i;
}
```

**[104. Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)**

![](Leetcode%20Pattern/2.jpeg)

#javascript #leetcode