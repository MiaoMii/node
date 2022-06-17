#### 加法 plus(n [, base])

```js
0.1 + 0.2                       // 0.30000000000000004
x = new BigNumber(0.1)
y = x.plus(0.2)                 // '0.3'
BigNumber(0.7).plus(x).plus(y)  // '1'
x.plus('0.1', 8)                // '0.225'
```

#### 减法 minus(n [, base])

```js
0.3 - 0.1                       // 0.19999999999999998
x = new BigNumber(0.3)
x.minus(0.1)                    // '0.2'
x.minus(0.6, 20)                // '0'
```

#### 乘法 times(n [, base]) ⇒ BigNumber; multipliedBy(n [, base]) ⇒ BigNumber

```js
0.6 * 3                         // 1.7999999999999998
x = new BigNumber(0.6)
y = x.multipliedBy(3)           // '1.8'
BigNumber('7e+500').times(y)    // '1.26e+501'
x.multipliedBy('-a', 16)        // '-6
```

#### 普通除法运算div(n [, base]) ⇒ BigNumber； dividedBy(n [, base]) ⇒ BigNumber

```js
x = new BigNumber(355)
y = new BigNumber(113)
x.dividedBy(y)                  // '3.14159292035398230088'
x.div(5)                        // '71'
x.div(47, 16)                   // '5'
//注意： 除法计算结果会根据DECIMAL_PLACES和ROUNDING_MODE两个属性设置进行舍入。
```

#### 除法，返回整数： idiv(n [, base]) ⇒ BigNumber；dividedToIntegerByv(n [, base]) ⇒ BigNumber

```js
x = new BigNumber(355)
y = new BigNumber(113)
x.dividedBy(y)                  // '3.14159292035398230088'
x.div(5)                        // '71'
x.div(47, 16)                   // '5'
```

#### 取模/取余： mod(n [, base]) ⇒ BigNumber；modulo.(n [, base]) ⇒ BigNumber

```js
1 % 0.9                         // 0.09999999999999998
x = new BigNumber(1)
x.modulo(0.9)                   // '0.1'
y = new BigNumber(33)
y.mod('a', 33)                  // '3'
```

#### 数字格式化 toFormat([dp [, rm]]) ⇒ string

```csharp
//返回字符串，会根据dp和rm进行舍入,并根据FORMAT属性进行格式化。
format = {
    decimalSeparator: '.',
    groupSeparator: ',',
    groupSize: 3,
    secondaryGroupSize: 0,
    fractionGroupSeparator: ' ',
    fractionGroupSize: 0
}
BigNumber.config({ FORMAT: format })
 
x = new BigNumber('123456789.123456789')
x.toFormat()                    // '123,456,789.123456789'
x.toFormat(1)                   // '123,456,789.1'
```

