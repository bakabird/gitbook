avalon的指令是一个非常重要的东西,它用来引入一些新的HTML语法, 使元素拥有特定的行为。 举例来说，静态的HTML不知道如何来创建和展现一个日期选择器控件。 让HTML能识别这个语法，我们需要使用指令。 指令通过某种方法来创建一个能够支持日期选择的元素。

指令一共拥有3种形式:


#指令

avalon的指令是一个非常重要的东西,它用来引入一些新的HTML语法, 使元素拥有特定的行为。 举例来说，静态的HTML不知道如何来创建和展现一个日期选择器控件。 让HTML能识别这个语法，我们需要使用指令。 指令通过某种方法来创建一个能够支持日期选择的元素。

指令一共拥有3种形式

##插值表达式

位于文本节点中的双重花括号,当然这个可以配置.此指令其中文本ms-text指令的简单形式.
```html
<p>{{@firstName+' '+@lastName}}</p>
```
插值表达式一般与带格式功能的过滤器一起使用.

##绑定属性

指元素节点以ms-开头的属性

绑定属性的属性名是以-分成几段 其中第二个就是指令的名字, 如ms-css, ms-attr, ms-html, ms-text, ms-on都是来源于jQuery同名方法名, 简单好记.

```html
<p ms-on-click="@clickFn" ms-if="@toggle">{{@name}}</p>
```                   
##自定义标签

以ms-开头的自定义标签, 我们需要用avalon.component方法定义它,然后在里面使用ms-widget指令 为它添加更多行为.

avalon.component方法有两个参数,第一个标签名,必须以ms-开头;第二个是配置对象.

配置对象里也有4个配置项

1. template,自定义标签的outerHTML,它必须是用一个普通的HTML元素节点包起来,里面可以使用`ms-*`等指令
2. defaults,用来定义这个组件的VM有什么属性与方法
3. soleSlot,表示自定义标签的innerHTML为一个默认的插入点 (或可理解为定义标签的innerHTML为当前组件某个属性的属性值) ,可选
4. getTemplate, 用来修改template, 依次传入vm与template, 返回新的模板. 可选,


