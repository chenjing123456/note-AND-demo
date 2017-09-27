#运算符

1.in运算符(判断是否是实例对象的自有属性或者继承属性)

  * 语法：'名字' in 对象
  * 返回值是boolean,  判断该名字是否存在一个属性与之相同

2.逻辑中断

  * ||和&&
  
     * ||第一个为真，则输出第一个值；第一位为假，则输出第二个值。
     * &&第一个为假，则输出第一个值；第一位为真，则输出第二个值。

3.delete运算符

  * 语法：delete 变量，数组项，对象属性
  
  * 返回值是boolean,    删除是否成功
  
4.面向对象

  * 面向对象是对面向过程（一步一步做）的封装，找一个对象并指挥它得到结果。

  * 面向（使用）对象开发：使用对象进行开发，如果系统有对象直接使用，如果没有则创建一个对象。
   
    * 先找对象，
   
    * 任何操作都应该交给对象做
    ```
    eg:创建一个div 加到body，并设置样式
      1.抽取对象（名词提炼）div body
      2.分析属性和方法(动词提炼)：加到，设置样式
    ```

  * js是基于对象的多范式（多种解决方法）编程。
  
  * 面向对象的特性
  
     * 抽象性：抽取对象的核心数据，并且不在特定条件下不知道是什么。
     * 封装性：将数据和功能（属性和方法）组合在一起
     * 继承性:别人有自己没有的，拿过来成为自己的。是实现复用的一种手段，js中没有明确的继承方法，其中有一种最简单的继承方法是混入（mix）
    
```
    function mix(o1,o2){
		for(var j in o2){//遍历o2
			o1[j]=o2[j];
		}
	   }
	   var o1={name:"fhfur"};
	   var o2={age:15};
	   mix(o1,o2);
```

5.浏览器调试工具

  * IE浏览器：需要手动进行开始调试；如果要查看最后一个变量的值，需要在最后设置一个变量var _ =0,因为IE运行到最后一句时会直接结束。
 
  * 火狐：firebug
 
  * 谷歌：可以设置条件断点

6.码表：用来互相解码的规则

  * ASCII码表，美国,128个（0-127，7个二进制位），用一个字节表示（一个字节等于8个二进制位）
		  97---a
		  65---A
		  32---空格
		  48---0
		  49---1	
  
  * unicode编码：使用两个字节表示一个字符（文字，标点.......）。
  
  * utf-系列（统一转换格式），与asicc码重合的部分使用一个字节，汉字使用三个字节。
  
  * 提问：一个字符占几个字节，需要考虑编码
        
    * ASCII编码（美国）：一个英文字母，数字，英文标点符号都是一个字节（7个二进制位）
    * 双字节字符（各国）：与asicc码重合的都是一个字节，其余独有字符2个字节（gb1232）
    * unicode编码（世界统一）：任何字符都是2个字节
    * utf-8 编码（防止浪费资源）：与asicc码重合的部分使用1个字节，汉字使用3个字节。
  
  * byte比特：一般表示字节和字的时候考虑字节（byte）是8个二进制位，一个字（word）就是一个字符
  
7.基本数据类型和复合数据类型的内存逻辑结构

8.基本数据类型和复合数据类型的赋值特征

   * 基本数据类型：赋值后修改属性不会影响原对象的属性
   * 引用数据类型：赋值后修改属性会影响原对象的属性（赋的值是地址，指向同一个堆对象）
   
9.修改obj会影响o，所以引出深拷贝和浅拷贝

  * 浅拷贝：只对当前对象的属性进行copy,属性内有引用数据类型的不进行处理，只赋给地址
  
  * 深拷贝：对所有的引用数据类型都进行拷贝，内部的引用类型指向一个新对象，与原来的相互独立。

10.浅拷贝
```
var p={
		name:'zs',
		age:19,
		lightCopy:function(){
          //创建对象
          var temp={};
          // 复制属性
          for(var k in this){
          	temp[ k ]=this[ k ];
          }
          // 返回新对象
          return temp;
		}
	};
var p1=p.lightCopy();//浅拷贝
```

11.深拷贝
	```
	var deepCopy=function(){
	    //创建对象
		var temp={};
		// 复制属性
		for(var k  in this){
		if(typeof this[k ]==="object"){
		temp[k]=this[k].deepCopy();
		}
		else{
		temp[k]=this[k];
		}
		}
		// 返回新对象
		return temp;
	}
		var p={
			name="zf",
			age:29,
		  car:car
		}
		var car={
			name:"fjg"
		}
		p.deepCopy=deepCopy;
		car.deepCopy=deepCopy;

		var p2=p.deepCopy();
```

12.值类型和引用类型作为函数参数的特征
   
13.对象的动态特性

  * 在js中，用【对象.属性名=值】的方式动态添加属性.
  
  * 对象属性的访问形式：o.name 和关联数组 o["name"]，方括号里必须是字符串
  
  * 凡是需要给对象动态添加成员的时候，使用关联数组的语法
  
  * `o['name']=o.name.`
  
```
for(var k in p){//此处的k是（字符串）属性名
  if(typeof p[k]==="function"){
  //p[k]是指该对象的所有属性，如果此处用k会使他的值永远为字符串
  	p[k]();
  	}
  	else{
  		console.log(p[k]);
  	}
  }
```