---
layout: post
title: DevExtream学习2 
categories: 
- js
- DevExtream
tags: 
-js
-DevExtream
---  
 
**Application Project**
[http://js.devexpress.com/Documentation/Howto/SPA_Framework/Application_Project/?version=14_2](http://js.devexpress.com/Documentation/Howto/SPA_Framework/Application_Project/?version=14_2 "http://js.devexpress.com/Documentation/Howto/SPA_Framework/Application_Project/?version=14_2")

# 应用程序项目(Application Project) #

使用DevExtream框架开发的应用程序,是单页面应用程序(SPA),以下页面代码示例(包含2个视图)  

HTML  
    <!DOCTYPE html>
	<meta charset="utf-8" />
	<!-- Links to themes and styles -->
	<!-- Links to the required scripts -->
	<script type="text/javascript" src="/js/jquery-2.1.3.min.js"></script>
	<script type="text/javascript" src="/js/knockout-3.2.0.js"></script>
	<script type="text/javascript" src="/js/globalize.min.js"></script>
	<script type="text/javascript" src="/js/dx.phonejs.js"></script>
	<!-- Links to layouts -->   
	<script type="text/javascript">
	    window.AppNamespace = {};
	    $(function () {       
	        AppNamespace.app = new DevExpress.framework.html.HtmlApplication({
	            namespace: AppNamespace,
	            layoutSet: "simple"
	        });
	        AppNamespace.app.router.register(":view/:name", { view: "home", name: '' });
	        AppNamespace.app.navigate();
	    });
	    AppNamespace.home = function () {
	        var viewModel = {
	            //ViewModel Fields
	        };
	        return viewModel;
	    };
	    AppNamespace.anotherView = function (params) {
	        var viewModel = {
	            //ViewModel Fields
	        };
	        return viewModel;
	    };
	</script>
	</head>
	<body>
	    <div class="dx-viewport">
	        <div data-options="dxView : { name: 'home', title: 'Home' } " >
	            <div data-options="dxContent : { targetPlaceholder: 'content' } " >
	                <!--View markup-->
	            </div>
	        </div>
	        <div data-options="dxView : { name: 'anotherView', title: 'Another View' } " >
	            <div data-options="dxContent : { targetPlaceholder: 'content' } " >
	                <!--View markup-->
	            </div>
	        </div>
	    </div>
	</body>
	</html>
--  
是可以把所有内容放入一个页面,但再实际项目中很难维护这样的页面.你可以将js代码,html标签,css标签放入独立的文件,为了简化开发,我们建议你使用devExtream提供的项目模板,包含以下内容.  

•css - 子文件夹,包含所支持设备的样式  


•js -  子文件夹,包含必须的js库


•layouts - 子文件夹,包含预定义的布局(常在移动程序中使用)  


•views - 子文件夹,包含视图文件;


•index.js -  主页js,创建和配置html应用程序对象(HTMLApplication object)  


•index.html - 主页html,包含所有引用资源的程序页面.  


•index.css - 主页样式,包含应用程序定义的css样式   

这样的项目模板时可以直接使用的,它包含简单的视图,并包含所有需使用的资源,你可以在以下位置找到这个模板  

•如果是单独产品,在zip压缩文件中的template下的knockout文件夹中.   

•如果是所有产品,集成到了vs的项目模板中.   

阅读以下内容,学习一个devexteam项目的组成部分  
应用程序页面(Application Page)  

与项目模板匹配的,一个应用程序页面只包含必须的资源,如下所示:

HTML
	<!DOCTYPE html>
	<html>
	    <head>
	        <meta charset="utf-8" />
	        <!-- Styles should be linked here-->
	        <!-- Scripts -->
	        <script type="text/javascript" src="/js/jquery-2.1.3.min.js"></script>
	        <script type="text/javascript" src="/js/knockout-3.2.0.js"></script>
	        <script type="text/javascript" src="/js/globalize.min.js"></script>
	        <script type="text/javascript" src="/js/dx.phonejs.js"></script>
	        <!-- Layouts should be linked here -->
	        <!-- Separated application files should be linked here -->
	    </head>
	    <body>
	        //Here is the div to which the application's views are rendered
	        <div class="dx-viewport"></div>
	    </body>
	</html>
  
  
正如以上代码所示,页面的主体(body)包含一个使用的dx-viewport样式的div对象.这个对象被用来插入一个视图,可以有很多视图,当将view port替换为视图的时候,这个单页面程序被转换成一个多屏幕的应用程序  

脚本(Scripts)  
当开发一个devExteme项目时,以下库必须在主页中被引用.  
•jQuery version 2.0.1+  
•Knockout version 2.2.3+  
•globalize  
•PhoneJS/WebAppJS  

注意: 按以上顺序引入相应的库文件   

有两种提供引用连接的方式.  
使用本地脚本(Use Local Scripts)   
你可以下载这些文件,将他们放入你的项目中,然后提供本地的连接  
HTML
	<script src="js/jquery-2.1.3.min.js"></script>
	<script src="js/knockout-3.2.0.js"></script>
	<script src="js/globalize.min.js"></script>
	<script src="js/dx.phonejs.js"></script>

在项目模板中,所有的引用脚本都是放在js文件夹下,使用的本地脚本.  
使用在线连接(Use a CDN)  
当使用Content Delivery Network (CDN),可以提高你程序的性能,

HTML
	<script type="text/javascript" src="http://cdn3.devexpress.com/jslib/14.2.5/js/dx.phonejs.js"></script>
	<script type="text/javascript" src="http://cdn3.devexpress.com/jslib/14.2.5/js/dx.webappjs.js"></script>

另外也可以使用以下方式.  

HTML
	<link rel="text/css" href="http://cdn3.devexpress.com/jslib/14.2.5/css/dx.ios.default.js" />
	<!--PhoneJS culture dictionaries-->
	<script type="text/javascript" src="http://cdn3.devexpress.com/jslib/14.2.5/js/localization/dx.phonejs.de.js"></script>
	<!--Predefined layouts for views-->
	<script type="text/javascript" src="http://cdn3.devexpress.com/jslib/14.2.5/layouts/Navbar/NavbarLayout.js"></script>
	<link rel="text/css" href="http://cdn3.devexpress.com/jslib/14.2.5/layouts/Navbar/NavbarLayout.css"/>
 
主体和样式 

为了使你的应用程序在不同设备上本地化,必须提供相应的主题.devexteam包含一系列针对不同设备的主题,常用的light和dark主题是可用的,这些主题不针对特殊的设备,但在不同设备上看起来都还可以,在添加产品脚本链接之前添加所需的主题链接.  

HTML
	<link rel="stylesheet" type="text/css" href="css/dx.common.css" />
	<link rel="stylesheet" type="text/css" href="css/dx.spa.css" />
	<link rel="dx-theme" data-theme="android5.light" href="css/dx.android5.light.css" data-active="true" />
	<link rel="dx-theme" data-theme="android.holo-dark" href="css/dx.android.holo-dark.css" data-active="false" />
	<link rel="dx-theme" data-theme="android.holo-light" href="css/dx.android.holo-light.css*" data-active="false" />
	<link rel="dx-theme" data-theme="ios.default" href="css/dx.ios.default.css" />
	<link rel="dx-theme" data-theme="ios7.default" href="css/dx.ios7.default.css" />
	<link rel="dx-theme" data-theme="win8.black" href="css/dx.win8.black.css" data-active="true" />
	<link rel="dx-theme" data-theme="win8.white" href="css/dx.win8.white.css" data-active="false" />
	<link rel="dx-theme" data-theme="tizen.black" href="css/dx.tizen.black.css" data-active="true" />
	<link rel="dx-theme" data-theme="tizen.white" href="css/dx.tizen.white.css" data-active="false"/>
	<link rel="dx-theme" data-theme="generic.light" href="css/dx.light.css" data-active="true" />
	<link rel="dx-theme" data-theme="generic.dark" href="css/dx.dark.css" data-active="false" />  
这些文件在你的devexteme包中是可用的.  
dx.common.css文件和dx.spa.css文件包含应用程序所需的样式,跟所运行的设备无关.  
想学习预定义的主题和样式,阅读相应的文章.  

除了预定义样式外,你可能还需要定义项目所需的样式,这些样式可以在app.css文件中定义,这个文件需要在项目主页中被引用.   

HTML
	<link rel="stylesheet" type="text/css" href="app.css"/>

The app.css file and the predefined themes are added to the application template project and referenced in the application page.


Application Object


To configure the application and control its life cycle, an HtmlApplication object must be created using the document.ready event or the jQuery "$()" function. There should be an index.js file within the application project. The HTMLApplication object should be created in this file.


JavaScript
window.MyApp = {};
MyApp.$(function() {
    MyApp.app = new DevExpress.framework.html.HtmlApplication({
        namespace: MyApp
    });
});

The parameter of the HTMLApplication's constructor is a configuration object that is used to set up application options.

Using the HTMLApplication object, register a routing rule for the application, and navigate to the starting view.


JavaScript
$(function() {
    MyApp.app = new DevExpress.framework.html.HtmlApplication({
        //...
    });
    MyApp.app.router.register(":view", { view: "home"});
    MyApp.app.navigate();
});

The index.js file must be linked in the application page.

<script type="text/javascript" src="index.js"></script>

The application template project includes this file and has a reference to it within the application page.


Layouts


According to the framework's Views and Layouts concept, a screen is a combination of view and layout markup. Each screen has a common element such as a navigation bar or a toolbar. These elements are added to the layout markup, which is then applied to each displayed view. Since several different layouts can be used in an application, a layout set should be specified as an array assigned to the layoutSet configuration option of the application object. The framework comes with ready-to-use layout sets that are based on predefined layouts.


JavaScript
window.MyApp = {};
MyApp.$(function() {
    MyApp.app = new DevExpress.framework.html.HtmlApplication({
        namespace: MyApp,        
        layoutSet: DevExpress.framework.html.layoutSets['navbar'],
        navigation: [
            {
                title: "Home",
                onExecute: "#home",
                icon: "home"
            },
            {
                title: "About",
                onExecute: "#about",
                icon: "info"
            }
        ]
    });
});

In the code above, the navigation option is specified. The array assigned to this option will be used by the 'navbar' predefined layout to create navigation items on the navbar widget.

The predefined layouts that are used in the speciified layout set should be contained in the application and referenced in the application page.


HTML
<!-- Layouts -->
<script type="text/javascript" src="layouts/Navbar/NavbarLayout.js"></script>
<link rel="stylesheet" type="text/css" href="layouts/Navbar/NavbarLayout.css" />
<link rel="dx-template" type="text/html" href="layouts/Navbar/NavbarLayout.html"/>
<script type="text/javascript" src="layouts/Simple/Simple.js"></script>
<link rel="stylesheet" type="text/css" href="layouts/Simple/Simple.css" />
<link rel="dx-template" type="text/html" href="layouts/Simple/Simple.html"/>

The application template project includes a folder with all the predefined layouts. The 'navbar' layout set is specified for the application, and the corresponding layouts are referenced in the application page.

All the layouts are available for you within the your DevExtreme package.

To learn more about view and layout concepts, refer to the Views and Layouts article.

To learn about layout sets and predefined layouts, refer to the Built-in Layouts article.


视图(Views)  

视图定义了组成视图模板的html标签的一部分.为了定制化样式和体验(look and feel)视图模板可选择包含js脚本以及相关联的样式.视图模板中js脚本和样式需要在不同的文件中实现,所以一个视图将包含以下文件.  
•viewName.html(以视图名称命名的html)  
•viewName.js(以视图名称命名的js)  
•viewName.css(以视图名称命名的css)  

将这些文件放置在项目的views文件夹下,在主页面中引用这些文件.  

	<!-- HTML --><link rel="stylesheet" type="text/css" href="views/home.css" />
	<script type="text/javascript" src="views/home.js"></script>
	<link rel="dx-template" type="text/html" href="views/home.html"/>
	<link rel="dx-template" type="text/html" href="views/about.html"/>
应用程序模板项目所包含的视图文件夹下已包含三个简单的视图文件,这些文件在项目中被引用.  
 
学习更过有关 视图的内容,阅读视图和布局相关的文章.
















 