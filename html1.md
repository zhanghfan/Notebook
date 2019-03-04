# markdown语法

+ 字体操作

**加粗**  
*倾斜文字*  
***斜体下、加粗***

~~加删除线~~

>引用
>>引用
>>>引用

#### 分割线
---
***  
#### 图片
![图1](“C:\Users\zf888\Desktop\source\互联网开发笔记\1.jpg”)

##列表

1. pear
2. apple
3. bannana  

   1. 汤
   2. 皮皮
   3. 哈哈哈

      4. 小
      5. 逗逼


* 无序列表
- 无序列表
+ 无序列表


+ 表格


姓名|技能|排行
--|:--:|--:
刘备|哭|大哥
关羽|打|二哥
张飞|骂|三弟

姓名|年龄|称号
--|:--:|--:
汤宏达|25|浪里飞
徐浩|35|窝里横
张帆|88|牛逼


+ 代码

#### 单行代码

`这是一行代码`

`代码内容`

#### 多行代码

```
   diama
   daima
   daima;
   weishen1
```


## 流程图  

```flow
st=>start: 开始
op=>operation: My Operation
cond=>condition: Yes or No?
e=>end
st->op->cond
cond(yes)->e
cond(no)->op
&```

```flow
st=>start: 开始
op=>operation: My Operation
cond=>condition: Yes or No?
e=>end
st->op->cond
cond(yes)->e
cond(no)->op
&```


st=>start: 开始
e=>end: 结束
op=>operation: 我的操作
cond=>condition: 判断确认

st->op->cond
cond(yes)->e
cond(no)->op