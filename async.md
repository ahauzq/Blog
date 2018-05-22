浅析async用法
```
class Test {
    constructor() { //构造函数
    }
    init() {
          console.log(1111);
          this.foo();
    }
    async  foo() {
        let a = await this.getData1();
        console.log(a); // 第1秒时输出: getData1返回的结果
        let b = await this.getData2(a);
        console.log(b); // 第2秒时输出: getData2返回的结果
    }
    getData1(param){
        return new Promise((resolve) => {
            setTimeout(() => {
                param = {
                    a:1
                };
                resolve(param);
            }, 1000);
        });
    }
    getData2(param){
        return new Promise((resolve, reject) => {
            console.log('测试param:',param);
            setTimeout(() => {
                resolve({b:'成功了'});
            }, 1000);
        });
    }
}
new Test().init();
```