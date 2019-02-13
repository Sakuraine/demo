# JavaScript基础

## 引用类型

##### 

> map遍历

返回一个新的数组

```jsx
{['one', 'two'].map((type) => {
	const title = `hellow${type}`;
	return (
		<div>{title}</div>
	)
})}
```

> for...in

```js
for (value in Object) {
  
}
```

> for...of

```js
for (const item of Object) {
  
}
```

> forEach()

```
stringLIst.forEach()
```



## 字符串

**String.indexOf(String)**

> 返回值`Number`

‘ - ’ 在 str 字符串里第一次出现的索引

```js
const strindex = str.indexOf('-');
```

**String.lastIndexOf(String)**

> 返回值`Number`

‘ - ’ 在 str 字符串里最后一次出现的索引

```js
const strindex = str.lastIndexOf('-');
```

**String.substring(String, String)**

> 返回值`String`

str 字符串里索引 a 到 b 的字符

```js
const newStr = str.substring(a, b);
```

**String.parseInt(String, Number)**

>返回值`Number`

将`String`转换成10进制的`Number`

```js
const newStr = parseInt(str, 10);
```

**toFixed()**

> 返回值``

**String.match(String, Reg)**

>

## RegExp对象

### [正则](https://baike.baidu.com/item/正则表达式/1700215?fr=aladdin)

## js类型转换

### 显示转换

#### 转换为数值类型：

##### Number(mix)

> 可以将任意类型的参数mix转换为数值类型。

​	规则：

  - 如果是布尔值，true 和 false 分别被转换为 1 和 0
  - 如果是数字值，返回本身
  - 如果是 null，返回0
  - 如果是 undefined，返回 NaN
  - 如果是字符串
      - 如果字符串中只包含数字，则建起转换为十进制（忽略前导0）
      - 如果字符串中包含有效的浮点格式，将其转换为浮点数值（忽略前导0）
      - 如果是空字符串，将其转换为0
      - 如果字符串中包含非以上格式，则将其转换为 NaN
  - 如果是对象，则调用对象的 valueOf() 方法，然后然后依据前面的规则转换返回的值
      - 如果转换的结果是 NaN，则调用对象的 toString() 方法，再次依照前面的规则转换返回的字符串值。

##### parseInt(string, radix)

> 将字符串转换为整数类型的数值

规则：

 - 忽略字符串前面的空格，直至找到第一个非空字符
 - 如果第一个字符不是数字符号或者负号，返回NaN
 - 如果第一个字符是数字，则继续解析直至字符串解析完毕或者遇到一个非数字符号为止
 - 如果上步解析的结果以0开头，则将其当作八进制来解析；如果以0x开头，则将其当作十六进制来解析
 - 如果指定radix参数，则以radix为基数进行解析

##### parseFloat(string)

> 将字符串转换为浮点数类型的数值

规则：

- 它的规则与parseInt基本相同，但也有点区别：字符串中第一个小数点符号是有效的，另外parseFloat会忽略所有前导0，如果字符串包含一个可解析为整数的数，则返回整数值而不是浮点数值

#### 转换为字符串类型：

##### toString(radix)

> 除 undefined 和 null 的所有类型的值都具有 toString() 方法，其作用是返回对象的字符串表示

| 对象     | 操作                                                         |
| -------- | ------------------------------------------------------------ |
| Array    | 将 Array 的元素转换为字符串。结果字符串由逗号分隔，且连接起来。 |
| Boolean  | 如果 Boolean 值是 true，则返回 “true”。否则，返回 “false”。  |
| Date     | 返回日期的文字表示法。                                       |
| Error    | 返回一个包含相关错误信息的字符串。                           |
| Function | 返回如下格式的字符串，其中 functionname 是被调用 toString 方法函数的名称：function functionname( ) { [native code] } |
| Number   | 返回数字的文字表示。                                         |
| String   | 返回 String 对象的值。                                       |
| 默认     | 返回 “[object objectname]”，其中 objectname 是对象类型的名称。 |

##### String(mix)

> 将任何类型的值转换为字符串

规则：

- 如果有 toString() 法，则调用该方法（不传递radix参数）并返回结果
- 如果是null，返回"null"
- 如果是undefined，返回"undefined"

#### 转换为布尔类型：

##### Boolean(mix)

> 将任何类型的值转换为布尔值

规则：

- 以下值会被转换为false：false、”"、0、NaN、null、undefined，其余任何值都会被转换为true

### 隐式转换

> 在某些情况下，即使我们不提供显示转换，Javascript也会进行自动类型转换，主要情况有：

#### 乘除、减号运算符、取模运算符

这些操作符针对的是运算，所以他们具有共同性：如果操作值之一不是数值，则被隐式调用Number()函数进行转换。具体每一种运算的详细规则请参考ECMAScript中的定义。

##### 用于检测是否为非数值的函数：isNaN(mix)

> isNaN()函数，经测试发现，该函数会尝试将参数值用Number()进行转换，如果结果为“非数值”则返回true，否则返回false。


##### 递增递减操作符（包括前置和后置）、一元正负符号操作符


> 这些操作符适用于任何数据类型的值，针对不同类型的值，该操作符遵循以下规则（经过对比发现，其规则与Number()规则基本相同）：

规则：

- 如果是包含有效数字字符的字符串，先将其转换为数字值（转换规则同Number()），在执行加减1的操作，字符串变量变为数值变量。
- 如果是不包含有效数字字符的字符串，将变量的值设置为NaN，字符串变量变成数值变量。
- 如果是布尔值false，先将其转换为0再执行加减1的操作，布尔值变量编程数值变量。
- 如果是布尔值true，先将其转换为1再执行加减1的操作，布尔值变量变成数值变量。
- 如果是浮点数值，执行加减1的操作。
- 如果是对象，先调用对象的valueOf()方法，然后对该返回值应用前面的规则。如果结果是NaN，则调用toString()方法后再应用前面的规则。对象变量变成数值变量。

##### 加法运算操作符
> 加号运算操作符在Javascript也用于字符串连接符，所以加号操作符的规则分两种情况：

> 如果两个操作值都是数值

​	规则：

 - 如果一个操作数为NaN，则结果为NaN
 - 如果是Infinity+Infinity，结果是Infinity
 - 如果是-Infinity+(-Infinity)，结果是-Infinity
 - 如果是Infinity+(-Infinity)，结果是NaN
 - 如果是+0+(+0)，结果为+0
 - 如果是(-0)+(-0)，结果为-0
 - 如果是(+0)+(-0)，结果为+0

> 如果有一个操作值为字符串

​	规则：

- 如果两个操作值都是字符串，则将它们拼接起来
- 如果只有一个操作值为字符串，则将另外操作值转换为字符串，然后拼接起来
- 如果一个操作数是对象、数值或者布尔值，则调用toString()方法取得字符串值，然后再应用前面的字符串规则。
- 对于undefined和null，分别调用String()显式转换为字符串。


可以看出，加法运算中，如果有一个操作值为字符串类型，则将另一个操作值转换为字符串，最后连接起来。


#### 逻辑操作符（!、&&、||）
##### 逻辑非（！）操作符

> 首先通过Boolean()函数将它的操作值转换为布尔值，然后求反。

##### 逻辑与（&&）操作符

> 如果一个操作值不是布尔值时，遵循以下规则进行转换：

​	规则：

- 如果第一个操作数经Boolean()转换后为true，则返回第二个操作值，否则返回第一个值（不是Boolean()转换后的值）
- 如果有一个操作值为null，返回null
- 如果有一个操作值为NaN，返回NaN
- 如果有一个操作值为undefined，返回undefined

##### 逻辑或（||）操作符

> 如果一个操作值不是布尔值

​	规则：

- 如果第一个操作值经Boolean()转换后为false，则返回第二个操作值，否则返回第一个操作值（不是Boolean()转换后的值）
- 对于undefined、null和NaN的处理规则与逻辑与（&&）相同

#### 关系操作符（<, >, <=, >=）
> 与上述操作符一样，关系操作符的操作值也可以是任意类型的，所以使用非数值类型参与比较时也需要系统进行隐式类型转换：

规则：

- 如果两个操作值都是数值，则进行数值比较

- 如果两个操作值都是字符串，则比较字符串对应的字符编码值

- 如果只有一个操作值是数值，则将另一个操作值转换为数值，进行数值比较

- 如果一个操作数是对象，则调用valueOf()方法（如果对象没有valueOf()方法则调用toString()方法），得到的结果按照前面的规则执行比较

- 如果一个操作值是布尔值，则将其转换为数值，再进行比较

注：NaN是非常特殊的值，它不和任何类型的值相等，包括它自己，同时它与任何类型的值比较大小时都返回false。

#### 相等操作符（==）
相等操作符会对操作值进行隐式转换后进行比较：

​	规则：

- 如果一个操作值为布尔值，则在比较之前先将其转换为数值

- 如果一个操作值为字符串，另一个操作值为数值，则通过Number()函数将字符串转换为数值

- 如果一个操作值是对象，另一个不是，则调用对象的valueOf()方法，得到的结果按照前面的规则进行比较

- null与undefined是相等的

- 如果一个操作值为NaN，则相等比较返回false

- 如果两个操作值都是对象，则比较它们是不是指向同一个对象

## 时间戳用法

对比时间和当前时间

hash



## canvs画布

drawImage方法

## console对象

```js
console.log()
```

弹出输入的对象

```js
console.table()
```

已表格形式弹出对象

trim()

## 树状结构

```jsx
const Tree = (tree, bool = true) => {
  return tree.map((item) => {
		if (item.children) {
      return (
        <div style={{ paddingLeft: '20px' }}>
          <span value={item.id} title={item.name} key={item.id} disabled={bool && item.id === '0'} />
    			{Tree(item.children)}
      	</div>
      );
    }
    return <span value={item.id} title={item.name} key={item.id} />;
  });
};
```



发布订阅

```jsx
/**
* 发布订阅
* @param  {[type]} name [description]
* @param  {[type]} func [description]
* @return {[type]}      [description]
*/
static Observer = (() => {
	const callbacks = {};
  return {
    subscribe(name, func, context) { // 订阅
      callbacks[name] = { func, context };
      return function () { // 默认返回订阅
      	callbacks[name] = null;
      };
    },

    publish(name, ...param) { // 发布
      const { func, context } = callbacks[name];
      return func && func.apply(context, param);
    },

    unsubscribe(name, func) { // 取消订阅
      callbacks[name] = null;
      }
    };
})()
```



```js
/**
   * 改变字段
   * @param {[type]} e      事件
   * @param {[type]} field  字段名
   * @param {[type]} code   exam_code
   * @return {[type]}       [description]
   */
handleChengeMedicalTreatmentData = (e, field, code) => {
  const { dispatch, data, form } = this.props;
  const exam_item_list = data.medicalTreatment.exam_item_list;

  let dataList = [];
  // 修正参数
  // 如果e是undefined说明修改的是一系列参数
  if (typeof e === 'undefined') {
    // 找到具体数据
    dataList = exam_item_list.map((item) => {
      if (item.exam_code === code) {
        return { ...item, ...field };
      }
      return { ...item };
    });
  } else {
    // 参数修正
    // 判断value值是否史target对象
    const value = e.target ? e.target.value : e;
    // 找到具体数据
    dataList = exam_item_list.map((item) => {
      if (item.exam_code === code) {
        return { ...item, [field]: value };
      }
      return { ...item };
    });
  }
  // 修改字段值
  dispatch(changeMedicalTreatment({ exam_item_list: dataList }));
}
```

