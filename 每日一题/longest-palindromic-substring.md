# 最长回文字符串

太久不做算法题，脑子锈的非常厉害。

最简单，也是最常规的做法，就是找每个字符作为中心点的长度呀。然后将最长的字符串存下来。
```
var longestPalindrome = function(s) {
    let temp = '';
    for(let i = 0; i < s.length; i++) {
        let even = expandCenter(s, i, i);
        let odd = expandCenter(s, i, i+1);
        temp = even.length > temp.length ? even : temp;
        temp = odd.length > temp.length ? odd : temp;
    }
    return temp;
    function expandCenter(s, left, right) {
        while(left >=0 && right <= s.length && s[left] === s[right]){
            left--;
            right++;
        }
        return s.slice(left+1, right);
    }
};
```
这里同时涉及到了取局部字符串的几种方法。

slice、substr(即将被废弃，建议使用substring)、substring、splice（这是数组的提取方法。。。）
下面根据MDN的说明，我们一一来介绍这几个方法。
> str.slice(beginIndex[, endIndex]) （方括号的意思表示可选）
slice() 方法提取某个字符串的一部分，并返回一个新的字符串，且不会改动原字符串。
注意： slice() 提取的新字符串包括beginIndex但不包括 endIndex
>str.substring(indexStart[, indexEnd])
substring 提取从 indexStart 到 indexEnd（不包括）之间的字符