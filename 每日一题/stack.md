# 两个关于栈和递归的小题

1. 括号的匹配问题
[leetcode链接](https://leetcode-cn.com/problems/valid-parentheses/)
```
/**
 * @param {string} s
 * @return {boolean}
 */
var isValid = function(s) {
    let a= [];
    let couple = {')':'(',']':'[', '}':'{'};
    for(let i=0; i < s.length; i++) {
        if(i == 0 || ['(','{', '['].indexOf(s[i]) != -1) {
            a.push(s[i]);
        } else {
            if(a[a.length-1] == couple[s[i]]) a.pop() 
            else return false;
        }
    }
    return a.length ? false : true;
};
```
1. 数组flatten问题
> [1, [2, [3, [4, 5]]], 6] -> [1, 2, 3, 4, 5, 6]
> 这里明显是一个递归问题，如果是数组的话就继续调用函数
```
/**
 * @param {array} s
 * @return {array}
 */
var flatten = function(s) {
    let a= [];
    var flattenArray = (s) => {
        for(let i=0; i < s.length; i++) {
              if(Array.isArray(s[i])) {
                flattenArray(s[i])
              } else {
                a.push(s[i])
              }
        }
    }
    flattenArray(s);
    return a;
};
```

变种
展开数组，并且不能有重复
```
/**
 * @param {array} s
 * @return {array}
 */
var flatten = function(s) {
    let a= new Set();
    var flattenArray = (s) => {
        for(let i=0; i < s.length; i++) {
              if(Array.isArray(s[i])) {
                flattenArray(s[i])
              } else {
                a.add(s[i])
              }
        }
    }
    flattenArray(s);
    return a;
};
```
