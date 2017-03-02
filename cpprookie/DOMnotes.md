# DOM Script notes
---

I will finish DOM Script before 20170113  and update my notes everyday.


----

**Jeremy Keith**  拥抱object detection
---

javascript 被认为性能差的原因
---

1. 早期浏览器兼容性差,需要编写很多的浏览器嗅探 (browser sniffing)代码(用来探测浏览器的品牌各版本)
2. 用来做弹窗，名声臭了
3. 名字带Java想乘java的顺风车结果翻了车(大家认为脚本语言应该是轻量的)
4. js实现的网页访问性差，经常弹报错窗口

边角料
-----
1. css 2002 年的时候也没人鸟
2. DOM在2006年前也面对这样的情况(书籍出版日期是2006年)估计具体时间会再早一两年。Google通过Gmail带了一波节奏。
3. ajax的横空出世拯救了js 的颓势。


第0级DOM
---
javascript 的早期版本向程序员提供操控图像、表单的方法：
```
document.images[2]
documnet.forms["details"]
```
这种实验性质的*文档对象*被称为第0级DOM。



DHTML与浏览器冲突
---
1. dynamic HTML是由 HTML CSS javascript相结合的产物(这已经很逼近现代浏览器的实现手段了，问题在哪儿呢？)
2. 这种想法至停留在理论上，因为不同的浏览器实现和兼容的是不同的DOM，想要实现理想还得填浏览器大战挖出的坑。
3. Netscape的dom使用的是特有元素 **layer**，每个**layer**都有自己的ID `document.layers[myElement]`
   操作DOM的left属性时，使用 `document.layers[myElement].left`
4. 微软的实现方法是 `document.all[myElement].leftpos`
5. 浏览器的差异带来的影响简直恐怖，试想一下，如果一个简单的DOM操作需要针对不同的浏览器写若干个版本会是一件多么蛋疼的事。

- 因为浏览器的战争，DHTML很快就香消玉殒了。


DOM level 1
----
1. 上面的例子用web标准实现变成： `document.getELementById(myElement).style.left` *格式的统一*
2. DOM不再局限于浏览器，而是变成了API,可以在接触了DOM之后考虑 如何实现用`Python`解析**XML文档**
3. W3C对 **DOM** 的定义 ： 一个与系统和编程语言无关的接口，程序和脚本可以通过这个接口动态地对文档内容、样式、结构进行访问和修改。
4. DHTML 是 HTML CSS JavaScript 混合的产物，但真正把这些东西融合在一起的是DOM.

语法
---
- 语法就略过不表了，但是可以记录些有意思的东西。
- 比如编译型语言和解释型语言，作者做了个很有意思的比喻。人类语言就是一门解释型语言，当你在进行阅读时能把它翻译为思想，但是只有遇到错误的地方你才会停下来。而不是编译型语言那样一开始就会被检查出来。

---
- 看作者说着十年前的关于`javascript`的东西还是有些温情的。
- 之前的`JavaScript`也可以使用`<!-`单行注释，我在控制台中试过，但目前应该不行了。
- *我们将在后来用变量做一些有用的事，请大家耐心的读下去*。哈哈，温情的作者。
- `javascript`允许不声明变量就直接使用，这样会直接搞出一个全局变量出来。
- `javascript`既是弱类型语言也是动态语言。但本书的作者解释的弱类型语言可能不太准确，[详见](https://www.zhihu.com/question/19918532)
- 一个变量存储一组值，即为数组 *有待商榷*

```
  var sample = [];
  sample['name'] = 'fang';
	sample['character'] = 'kind';
```
+ 关联数组(associative Array)，关于作者提到的这个概念。似乎也有待商榷。
  + 上例中的示例代码，运行后可以在浏览器里看到sample的 `length` 依然为0，只是为sample定义了新的 `property`罢了。
	+ js中一切类型的原型都是 `Object` ， 所以 `Array`也自然继承了对象的属性。

- `javascript`没有块级作用域，只有 *函数内作用域* 和 *全局作用域*。
- `new`用来创建对象实例。 `new constructor[(arguments)]`，[详见](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Operators/new)
- 构造函数是原型的`prototype`的一个方法，通过构造函数形成新实例。
