###helloGenerator 用法一

```javascript
function* helloGenerator() {
    yield "hello";
    yield "world";
    return "Generator";
}

var hg = helloGenerator();
console.log(hg);
//一次next之后值
var val = hg.next();
console.log("第1次next之后值", val.value);
console.log("第1次next之后状态", val.done);
//一次next之后值
console.log("第2次next之后值", hg.next().value);
//一次next之后值
var endVal = hg.next();
console.log("第3次next之后值,应该是retrun的值，并且当前的状态是true", endVal.value, endVal.done);
//值
console.log("第4次next之后值,此时什么都没有了", hg.next().value);
```

###helloGenerator 用法二

```javascript
var hg;
function* helloGenerator() {
    const A = yield new Promise((resolve, reject) => {
        console.log("1");
        setTimeout(() => {
            resolve("Promise1");
            hg.next("PromiseA");
        }, 3000);
    });
    console.log("aaaa", A);
    const B = yield new Promise((resolve, reject) => {
        console.log("2");
        setTimeout(() => {
            resolve("Promise2");
            hg.next("PromiseB");
        }, 1000);
    });
    console.log("bbbbb", B);
}
hg = helloGenerator(hg);
hg.next();
```

###数组去重并且把最新的数字插入末尾

```javascript
var removeDuplicates = function(nums, val) {
    //nums.push(val);
    nums = nums.filter(item => {
        return item !== val;
    });
    nums.push(val);
    return nums;
};

console.log(removeDuplicates([1, 2, 3, 2, 2, 2, 4], 2));
```

###defineProperty

```javascript
var person = {
    a: 1
};
Object.defineProperty(person, "a", {
    get() {
        return this.a;
    },
    set(val) {
        this.a = val;
    }
});
```

###正则替换

```javascript
var s =
    'aa<style>.contract-checkbox-image { margin-bottom: -3px; }.contract-small-input { display: inline-block; min-width: 100px; border-bottom: 1px solid #cccccc; word-break: break-all;text-align: left;}.contract-medium-input {display: inline-block; min-width: 210px; border-bottom: 1px solid #cccccc; word-break: break-all;text-align: left;}.contract-large-input {display: inline-block; min-width: 500px; border-bottom: 1px solid #cccccc; word-break: break-all;text-align: left;}.contract-time-picker {display: inline-block; min-width: 150px; border-bottom: 1px solid #cccccc; text-align: left;cursor: pointer;}.contract-date-picker {display: inline-block; min-width: 110px; border-bottom: 1px solid #cccccc; text-align: left;cursor: pointer;}.contract-checkbox-input {position: absolute; left: -9999px;}.contract-checkbox-container {display: inline-block; position: relative; vertical-align: middle; font-family: sans-serif;}body { font-size: 14px; font-family: SimSun, 宋体; }.checkbox-marker {display: inline-block; box-sizing: border-box; width: 16px; height: 16px;border-radius: 2px; margin-right: 8px; cursor: pointer;}content: ""; position: absolute;width: 3px; height: 6px; border: solid white; border-width: 0 2px 2px 0;-webkit-transform: rotate(45deg); -ms-transform: rotate(45deg); transform: rotate(45deg);}</style>bb';
s = s.replace(/<style>[\s\S]*?<\/style>/gi, "");
console.log(s);
```

###正则小数拦截

```javascript
function amount(v) {
    var regStrs = [
        ["^0(\\d+)$", "$1"], //禁止录入整数部分两位以上，但首位为0
        ["[^\\d\\.]+$", ""], //禁止录入任何非数字和点
        ["\\.(\\d?)\\.+", ".$1"], //禁止录入两个以上的点
        ["^(\\d+\\.\\d{2}).+", "$1"] //禁止录入小数点后两位以上
    ];
    for (i = 0; i < regStrs.length; i++) {
        var reg = new RegExp(regStrs[i][0]);
        v = v.replace(reg, regStrs[i][1]);
    }
    return v;
}
```

###模板字符串替换

```javascript
function parseString(str, obj) {
    Object.keys(obj).forEach(key => {
        str = str.replace(new RegExp(`{{${key}}}`, "gm"), obj[key]);
    });
    return str;
}
var str = "{{name}}很厉name害{{name}}，才{{age}}岁";
var obj = { name: "张三", age: "15" };
console.log(parseString(str, obj));
```
