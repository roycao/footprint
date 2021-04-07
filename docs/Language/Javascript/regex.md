# 正则表达式

## 断言
**系统断言**
- ^: 匹配字符串开始位置
- $: 匹配字符串结束位置
- \b: 匹配字符的界限
- \B: 与\b相反，匹配非字符的界限 

****
- **先行断言**

语法：x(?=y)  
解释：x被y跟随时，匹配x
```javascript
   let m = 'ababbcd'.match(/b+(?=c)/)
   m//[bb]
```
- **后行断言**
语法：(?<=y)x  
解释：y出现在x的前面，匹配x  
```javascript
   let m = 'ababbcd'.match(/(?<=ab)b/)
   m//[第三个b]
```
- **先行否定断言**

语法：x(?!y)  
解释：x不被y跟随时，匹配x
```javascript
   let m = 'ababbcd'.match(/b+(?!c)/)
   m//[b]
```

- **后行否定断言**

语法：(?<!y)x  
解释：y不出现在x的前面，匹配x
```javascript
   let m = 'ababbcd'.match(/(?<!ab)b/)
   m//[第一个b]
```
[//]:~~*例子*~~ 

## 实战 
>1.实现千分位分隔符
```javascript
function evRegex(num){
    let result = num.toString().replace(/\d+/,function(match){
        return match.replace(/(\d)(?=(\d{3})+$)/g, function($1){
            return $1+",";
        });
    })

    return result;
}
evRegex(12324111.34322)
```