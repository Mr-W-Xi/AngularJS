#AngularJS
AngularJS 通过新的属性和表达式扩展了 HTML。  
AngularJS 可以构建一个单一页面应用程序
#####使用：
- 引入**angular.min.js**文件或指定版本
- 在html中添加ng-app="myapp" 例：< html ng-app="myapp(这里的名字自定义)"> ng代表angular 、 app 代表了appliction应用
- 是在视图层view（html）操作,**视图html(view)只是负责显示,尽量不要写业务逻辑**
###表达式
- AngularJS 表达式写在双大括号内：{{ expression }}。
- AngularJS 将在表达式书写的位置"输出"数据。
- **AngularJS 表达式** 很像 **JavaScript 表达式**：它们可以包含文字、运算符和变量。  
实例 {{ 5 + 5 }} 或 {{ firstName + " " + lastName }}

#####总结：


- 表达式里面可以使用运算符，逻辑运算符等等，**不能使用**流程控制语句，alert、函数
##JS部分
- 1.// var app=angular.module("ng-app的名字",[]);

		var app=angular.module("myapp",[]);


- 2.// app.controller("控制器的名字",fn($scope){})

		app.controller("cont1",function($scope,$rootScope){...}  
		//$scope是固定写法  
		//控制器取值范围对应视图ng-controller的节点范围
		
- 3.//$scope.set//函数名=function(){}

		函数写法$scope.函数名=fn（）{}
- **在angular中必须遵循angular和原生js的写法，在页面中写的东西都要被app.controller)("",fn(){里面写内容})包裹**
- **小知识 $rootScope是跨作用域使用的**

	$rootScope 可作用于整个应用中。是各个 controller 中 scope 的桥梁。用 rootscope 定义的值，可以在各个 controller 中使用。
##指令
- **angular里面所有的指令都是ng开头**
- **ng-app 指令**

	ng-app 指令定义了 AngularJS 应用程序的 根元素。     
    （ng-app 定义了 浏览器从哪开始解析 angular）    	 
	ng-app 指令在网页加载完毕时会自动引导（自动初始化）应用程序。
- **ng-init 指令**

	ng-init 指令为 AngularJS 应用程序定义了 初始值。
	通常情况下，不使用 ng-init。您将使用一个控制器或模块来代替它。

- **ng-model 指令**

	用于绑定应用程序到HTML控制器（input、select、textarea）的值  
	ng-model是用于表单元素的，支持双向绑定。对普通元素无效；  
	ng-model是双向绑定在修改输入域的值时，Angular属性也将修改；   
	ng-model 指令 绑定 HTML 元素 到应用程序数据。  
	ng-model 指令也可以：  
	1.为应用程序数据提供类型验证（number、email、required）  
	2.为应用程序数据提供状态（invalid、dirty、touched、error）  
	3.为 HTML 元素提供 CSS 类。  
	4.绑定 HTML 元素到 HTML 表单
- **ng-bind 指令** 

	ng-bind 指令告诉 AngularJS 使用给定的变量或表达式的值来替换 HTML 元素的内容  
	当Ng-bind和{{}}同时使用，ng-bind绑定的值覆盖该元素的内容  
	ng-bind用于普通元素，不能用在表单元素  
	（ng-bind="" 双引号里面注意类型）  
#######案例：   
	< div ng-init="one={name:'松淫',year:'18',sex:'未知',url:'images/1.jpg',href:'http://www.baidu.com'}">  
		<h1 ng-bind="'ok'"></h1>  
		<!-- ng-bind=""双引号里面要注意类型 -->  
		<p ng-bind="one.name"></p>  
		<p ng-bind="one.year"></p>  
		<img ng-src="{{one.url}}" alt="">  
		< a href="{{one.href}}" title="{{'点击跳转'}}">跳转< /a>  
	< /div>
- **ng-controller 指令**

	ng-controller 指令用于为应用添加控制器。  
	在控制器中，你可以编写代码，制作函数和变量，并使用 scope 对象来访问。  
	语法<element ng-controller="expression"></element>

- **ng-repeat 指令**

	用于循环输出指定次数的HTML元素  
######例如：
	ng-repeat=" item in data"参数固定（x in 数组或对象）  
	 	<li ng-repeat="item in data">  
			< h1>{{item.name}}< /h1>  
			< p>{{item.sex}}< /p>  
			< img ng-src="{{item.img}}" alt="">    
			< p>说:{{item[0][0]}}< /p>  
			< p>年龄:{{item.year}}< /p>  
		< /li>

- **ng-style 指令**

	可以加控制器里面键值对表示的样式  
	ng-style 指令为 HTML 元素添加 style 属性。  
	ng-style 属性值必须是对象，表达式返回的也是对象。

- **ng-click 指令**

	单击指令 同点击事件一样
- **ng-src 指令**

	ng-src 指令覆盖了 <img> 元素的 src 属性。  
	如果你使用了 AngularJS 代码设置图片地址，请使用 ng-src 指令替代 src 属性。  
	ng-src 指令确保的 AngularJS 代码执行前不显示图片  
	语法：<img ng-src="string">< /img>

- **ng-show / ng-hide  指令**.

	ng-show=" " 显示节点，双引号里面传一个布尔值  
	ng-hide=" " 隐藏节点，双引号里面传一个布尔值
- **ng-class 指令**

	ng-calss=" "双引号里面是一个键值对，{类名：布尔值类型}

	例如：ng-class="{col1:$first,col2:$middle,col3:$last}"

- **ng-options 指令**

	ng-options 指令用于使用 < options> 填充 < select> 元素的选项。
  
######例：  


	<se lect ng-model="v1" ng-options="val.a for val in data" ng-change="test(v1)">  
		<!-- ___val.a for为了在option里面显示__ val(去壳) in data -->  
		<!-- v1就是  中间的val -->  
		<opt ion value="">全部</op tion>  
	</se lect>  
	<!-- {a:'上海',b:[
		 			{c:'上海',e:['浦东新区','黄浦区','青浦区','卢湾区','闸北区','静安区']}
		 				]
		 		     }, -->
	<sel ect ng-model="v2" ng-options="val.c for val in v1.b" ng-change="test(v1)">  
		<op tion value="">全部</opt ion>  
	</se lect>  
	<se lect ng-model="v3" ng-options="val for val in v2.e" ng-change="test(v1)">  
		<opt ion value="">全部</opt ion>  
	</se lect>  
	Javascript  部分
		var app=angular.module("myapp",[]);
		app.controller("cont",function($scope){  
			$scope.data=  
 				[
		 			{a:'上海',b:[
		 				{c:'上海',e:['浦东新区','黄浦区','青浦区','卢湾区','闸北区','静安区']}
		 				]
		 		     },
		 	        {a:'北京',b:[{c:'北京',e:['东城区','西城区','崇文区','宣武区','朝阳区']}
		 	            ]
		 	         },
		            {a:'湖北',b:[{c:'武汉',e:['江岸区','江汉区','硚口区','武昌区','洪山区']},
		            {c:'襄阳',e:['襄城区','樊城区','襄州区','枣阳市','南漳县','保康县','老河口市']},
		            {c:'北平',e:['朝阳','老城区']}
		                ]
		            }
		 		];  

			$scope.test=function(val){  
				console.log(val);  
			}  
		})  
- **ng-switch 指令**  
	
	ng-switch 指令根据表达式显示或隐藏对应的部分。    
	对应的子元素使用 ng-switch-when 指令，如果匹配选中选择显示，其他为匹配的则移除。    
	你可以通过使用 ng-switch-default 指令设置默认选项，如果都没有匹配的情况，默认选项会显示    
	语法  
	
	
		<element ng-switch="expression">  
		.   <element ng-switch-when="value">< /element>  
		.   <element ng-switch-when="value">< /element>  
		.   <element ng-switch-when="value">< /element>  
		.   <element ng-switch-default></element>  
		< /element>
	
##过滤器
	过滤器使用一个管道字符（|）添加到表达式和指令中。  
	
<table>
 <tr>AngularJS 过滤器可用于转换数据（内置过滤器）：
  <td>currency货币格式化</td>
  <td>格式化数字为货币格式。</td>
 </tr>
 <tr>
  <td>filter查找</td>
  <td>从数组项中选择一个子集。该过滤器后跟一个冒号和一个模型名称。</td>
 </tr>
 <tr>
  <td>lowercase</td>
  <td>格式化字符串为小写。</td>
 </tr>
 <tr>
  <td>orderBy</td>
  <td>根据某个表达式排列数组。</td>
 </tr>
 <tr>
  <td>uppercase</td>
  <td>格式化字符串为大写。</td>
 </tr>
<tr>
  <td>limitTo 截取</td>
  <td>截取数据 {{"123456" | limitTo :2/-2}} // 从前面/后面开始截取2位</td>
 </tr>
</table>

#####时间 date格式化  

	{{149016 | date:"yyyy-MM-dd HH:mm:ss"}} // 2017-06-15 10:09:25  
	app.controller("cont",function($scope,$interval){  
		var timer=$interval(function(){  
				$scope.timer=new Date();  
			},1000/24)  
	})  
	
>$interval  

	$interval是angular独有的自带的定时器  
#####number 格式化（保留小数）  

	{{149016.1945000 | number:2}}  
	
#####filter查找  

	filter 过滤器从数组中选择一个子集  
	// 查找name为iphone的行  
	
	
		{{ [{"age": 20,"id": 10,"name": "iphone"},  
		{"age": 12,"id": 11,"name": "sunm xing"},  
		{"age": 44,"id": 12,"name": "test abc"}  
		] | filter:{'name':'iphone'} }}       
#####orderBy 排序  

	// 根id降序排  
	
		{{ [{"age": 20,"id": 10,"name": "iphone"},  
		{"age": 12,"id": 11,"name": "sunm xing"},  
		{"age": 44,"id": 12,"name": "test abc"}  
		] | orderBy:'id':true }}  
	
	// 根据id升序排  
	
		{{ [{"age": 20,"id": 10,"name": "iphone"},  
		{"age": 12,"id": 11,"name": "sunm xing"},  
		{"age": 44,"id": 12,"name": "test abc"}  
		] | orderBy:'id' }}  
##自定义过滤器  

	app.filter("过滤器名字",function(）{    
		return function（val）{    
			return val管道符前面的值} )}  
>案例  

	app.filter("test",function(){
			return function(val){
				console.log(val);  // val是管道符前面的值
				// console.log(year);   year 是冒号后面的值
				return val+"是:"+typeof val+"类型";
			}
		})
##表单  

AngularJS 表单是输入控件的集合。 

####数据绑定  

Input 控件使用 ng-model 指令来实现数据绑定。  

	<input type="text" ng-model="firstname">  
	
#####Checkbox（复选框）  

checkbox 的值为 true 或 false，可以使用 ng-model 指令绑定，它的值可以用于应用中：  
 
	复选框选中后显示 h1 标签内容：  
	
	< form>
	    <input type="checkbox" ng-model="myVar">
	< /form>
	 
	<h1 ng-show="myVar">My Header</h1>
#####单选框  

我们可以使用 ng-model 来绑定单选按钮到你的应用中。 

单选框使用同一个 ng-model ，可以有不同的值，但只有被选中的单选按钮的值会被使用。  

	根据选中的单选按钮，显示信息：
	< form>
    选择一个选项:
    <input type="radio" ng-model="myVar" value="dogs">Dogs
    <input type="radio" ng-model="myVar" value="tuts">Tutorials
    <input type="radio" ng-model="myVar" value="cars">Cars
	< /form>
#####下拉菜单  

使用 ng-model 指令可以将下拉菜单绑定到你的应用中。 

ng-model 属性的值为你在下拉菜单选中的选项：    
	
	根据选中的下拉菜单选项，显示信息：
	<form>
	选择一个选项:
	<select ng-model="myVar">
	    <option value="">
	    <option value="dogs">Dogs
	    <option value="tuts">Tutorials
	    <option value="cars">Cars
	</select>
	</form>
	
	
#####表单案例  
	
		<f orm name="myform">
			<input type="text" name="user" ng-model="test1" required ng-pattern="/[0-9]{3}/">
			<!-- angualr ng-pattern="/[0-9]{3}/" -->
			<input type="text" name="user1" ng-model="test2">
			<hr>
				<!-- 名字 form下面 user--> 
			<span>未修改状态:{{myform.user.$pristine}}</span>
			<span>未修改状态:{{myform.user1.$pristine}}</span>
	
			<hr>
			<span>
				已修改状态:{{myform.user.$dirty}}
			</span>
			<hr>
			<span>
				通过验证:{{myform.user.$valid}}
			</span>
			<span>
				不通过验证:{{myform.user.$invalid}}
			</span>
			<button ng-disabled="myform.user.$invalid">提交</button>
		</f orm>
	javascript部分
			var app=angular.module("myapp",[]);
		

#####AngularJS输入验证（上面有案例） 


	1.$dirty      表单填写记录  
	2.$valid		字段内容合法  
	3.invalid		字段内容是非法的  
	4.pristine	表单没有填写记录  
	
	


##AngularJS 路由  


1.AngularJS 路由允许我们通过不同的 URL 访问不同的内容。 

2.通过 AngularJS 可以实现多视图的单页Web应用（single page web application，SPA）。  

3.通常我们的URL形式为 http://runoob.com/first/page，但在单页Web应用  
中 AngularJS 通过 # + 标记 实现 例如：  
	
		http://runoob.com/#/first  
		http://runoob.com/#/second  
		http://runoob.com/#/third  
	
4.当点击以上的任意一个链接时，向服务端请的地址都是一样的 (http://runoob.com/)。  
因为 # 号之后的内容在向服务端请求时会被浏览器忽略掉。 所以就需要在客户端实现 # 号后面
内容的功能实现。  

5.路由 属于angularJS的扩展，需要额外引入文件 angular-route.js  

6.注意 注意：路由可以是并列关系的节点，指令是包裹关系的节点（写在一个div里面） 

7.路由要写在控制器前面  

8.templateUrl:path 加载页面需要在服务器下面测试。例： 
	
		.when("/"
			{templateUrl:"tmpl/index.html //路径"
			})  
		
**主要思想**：使用路由器时，一定要把所有页面想象成一个页面。（在服务器下面测试）  

	
实例解析：
1、载入了实现路由的 js 文件：angular-route.js。

2、包含了 ngRoute 模块作为主应用模块的依赖模块。
	angular.module('routingDemoApp',['ngRoute'])
	
3、使用 ngView 指令。
	<div ng-view></div>
	该 div 内的 HTML 内容会根据路由的变化而变化。
	
4、配置 $routeProvider，AngularJS $routeProvider 用来定义路由规则。

	module.config(['$routeProvider', function($routeProvider){
	  $routeProvider
	.when('/',{template:'这是首页页面'})
	.when('/computers',{template:'这是电脑分类页面'})
	.when('/printers',{template:'这是打印机页面'})
	.otherwise({redirectTo:'/'});
	}]);
	
AngularJS 模块的 config 函数用于配置路由规则。通过使用 configAPI，我们请求把$routeProvider注入到我们的配置函数并且使用$routeProvider.whenAPI来定义我们的路由规则。

$routeProvider 为我们提供了 when(path,object) & otherwise(object) 函数按顺序定义所有路由，函数包含两个参数:
	第一个参数是 URL 或者 URL 正则规则。
	第二个参数是路由配置对象。
路由设置对象
AngularJS 路由也可以通过不同的模板来实现。
$routeProvider.when 函数的第一个参数是 URL 或者 URL 正则规则，第二个参数为路由配置对象。
	路由配置对象语法规则如下：
		
		$routeProvider.when(url, {
		    template: string,
		    templateUrl: string,
		    controller: string, function 或 array,
		    controllerAs: string,
		    redirectTo: string, function,
		    resolve: object<key, function>
		});
	
	参数说明：
		template:
			如果我们只需要在 ng-view 中插入简单的 HTML 内容，则使用该参数：
			
				.when('/computers',{template:'这是电脑分类页面'})
		templateUrl:
			如果我们只需要在 ng-view 中插入 HTML 模板文件，则使用该参数：
			
				$routeProvider.when('/computers', {
	  			  templateUrl: 'views/computers.html',
				});
	以上代码会从服务端获取 views/computers.html 文件内容插入到 ng-view 中。
	
	controller:
	
		function、string或数组类型，在当前模板上执行的controller函数，生成新的scope。
		
	controllerAs:
	
		string类型，为controller指定别名。
	redirectTo:
	
		重定向的地址。
	resolve:
	
		指定当前controller所依赖的其他模块。
	
**写法：**  

	angular路由写法 -->
		<a href="#/">首页</a>
		<a href="#/list">列表页</a>
		<a href="#/show">显示页</a>
		<a href="#/test">没有</a>
	<div ng-view></div> //必须写（固定写法ng-view）

	<script>
		// var app=angular.module("myapp",['扩展'//带引号],函数名);
		var app=angular.module("myapp",['ngRoute'],RouterConfig);
		function RouterConfig($routeProvider){
			// $routeProvider路由提供者//配置 $routeProvider，AngularJS $routeProvider 用来定义路由规则。
			$routeProvider
				.when("/",
					{template:"<h1>我是首页</h1>"
				})
				.when("/list",
					{template:"<h1>我是列表页</h1>"
				})
				.when("/show",
					{template:"<h1>我是显示页面</h1>"
				})
				.otherwise({
					//如果没有路由就在这
					template:"<h1>404页面</h1>"
				})
		}    //（上）路由要写在控制器前面（下）
		app.controller("cont",function($scope){
			$scope.info="我是控制器数据";
			$scope.show=function(){
				alert($scope.info);
			}
		})
###指令系统（自定义指令系统）  
	
	指令是一个封装好的功能,通过写在,视图的节点上,达到功能无限的复用
	
#####限制使用  

	实例
	通过添加 restrict 属性,并设置只值为 "A", 来设置指令只能通过属性的方式来调用:
	var app = angular.module("myApp", []);
	app.directive("runoobDirective", function() {
	    return {
	        restrict : "A",//注释指令加replace:true,
	        template : "<h1>自定义指令!</h1>"
	    };
	});

	restrict 值可以是以下几种:
	E 作为元素名使用
	A 作为属性使用
	C 作为类名使用
	M 作为注释使用  需要加replace:true
	restrict 默认值为 EA, 即可以通过元素名和属性名来调用指令。
	// 推荐使用 AE两种类型
	//推荐使用replace:true,
######自定义指令  
	
使用 .directive 函数来添加自定义的指令。    
要调用自定义指令，HTML 元素上需要添加自定义指令名。    
使用驼峰法来命名一个指令， **runoobDirective**, 但在使用它时需要以 - 分割, **runoob-directive**:  
	
	AngularJS 实例
	<body ng-app="myApp">	
	<runoob-directive></runoob-directive>
	<script>
	var app = angular.module("myApp", []);
	app.directive("runoobDirective", function() {
	    return {
	        template : "<h1>自定义指令!</h1>"
	    };
	});
	</script>
	</body>
你可以通过以下方式来调用指令：（这些方式也能输出同样结果）  
	
	元素名  <runoob-directive></runoob-directive>
	属性    <div runoob-directive></div>
	类名    <div class="runoob-directive"></div> 
	注释    <!-- directive: runoob-directive --> 注释指令需要必须加  
			replace:true属性 推荐 加 template:"<h1>我是指令系统</h1>",
###**注意:路由可以试并列关系的节点,指令是包裹关系的节点**  
	
	路由：
		<a href="#/">
		<a href="#/list>
	指令：
	<div>
		<dirce></dirce>
		<div dirce><dirce>
	</div>//必须是包裹关系

##angular中的compile和link函数  
	
	指令函数：
		compile：function（）{}//compile选项可以返回一个对象或函数。
		link：function（scope,iEle,iAttrs,ctrl,linker）{}//link函数主要用于操作dom元素,给dom元素绑定事件和监听.


	compile 选项本身并不会被频繁使用，但是 link 函数则会被经常使用。
	
![](http://a2.qpic.cn/psb?/V12rzXyJ2EqKG8/jwjj2E66CtkuRdpGnFePGd4exOuuQh.T3HfL.FnaE5w!/b/dD8BAAAAAAAA&bo=1wSAAgAAAAADB3M!&rf=viewer_4)
	
	当设置了link选项，实际上是创建了一个postLink() 链接函数，以便compile() 函数可以定义链接函数。编译函数(compile)负责对模板DOM进行转换。
	链接函数(link)负责将作用域和DOM进行链接。

####link函数  
	
	// controllerAs控制器名字
				controllerAs:"linker",
	link:function(scope,iElement,iAttrs,ctrl,linker){....}


	
	link属性值为一个函数,这个函数有五个参数:scope,iEle,iAttrs,ctrl,linker

	scope:指令所在的作用域,这个scope和指令定义的scope是一致的.//指令系统存放数据区$scope上面的数据
	
	iElement:指令元素的jqLite封装.//div元素
	
	iAttrs:指令元素的属性的集合//div上的属性
	
	ctrl:需要和require属性一起使用,用于调用其他指令的方法,指令之间的互相通信,这个在讲require属性的时候会详细解释
	
	linker:控制器名字//this绑定值，也是数据区上的数据
	（// linker  与  scope区别就是两个绑定的空对象，
	//一个指向this//一个指向$scope）


					



	
