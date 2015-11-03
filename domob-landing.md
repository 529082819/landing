##<center><b><strong>Landing 品牌广告上线注意事项

1、资源图片文件的放置
	
	所有的banner、cp、视频、音频、大图片、凡是较大的资源文件都要上传到cdn服务器（广告服务器）进行投放
	上传脚本 ./deploy_sm.sh 文件夹名称 
	

2、接口调用注意

	banner类的展现广告不要进行调用第三方的免费接口，
	因为banner的展现量会很大达到上亿的级别。
	第三方发现后会进行封禁的。如调用百度的地图API进行位置距离的转化等。
	
	
3、Landing的图片上传限制 （50张 10M）

	上传脚本 ./deploy_deploy_moxzcn201403.sh 文件夹名称 
	Landing广告不能上传视频、音频文件、
	图片大于50张或者图片资源的大小超过10M的话：
	（上线会提示yes/no，选择yes继续上传会邮件警告，选择no不上传）
	可把资源放到cdn（广告服务器）上。
	
	
##<center>Landing Page注意事项

1、如需监测pv、uv、注册数据、点击数据等，必须在head添加一段js

	<script type="text/javascript" id="domob_landing" src="http://service.moxz.cn/landingjs/landing-v5.3.1.js?landingid=39hLnJ9vBjkVcA&pageid=index&rescale=0"></script>
	
	landingid需在back后台生成的、
	pageid根据页面随意命名、
	rescale=0表示页面不缩放（一般情况下不加）
	
2、以前做过的一些 [landing demo](http://duomeng.cn/design_demo2/) 点击可查看

3、大型项目（几个人一起做的）使用svn修改项目前注意要update，避免svn报错

##<center>landing-v5.3.1.js的一些方法

1、增加参数 extend=call_share   

	作用是增加拨打电话以及分享的功能 (如果没有拨打电话和分享可不引用)
	
	例如:http://service.moxz.cn/landingjs/landing-v5.3.1.js?landingid=39hLlJ9RBjkzIC&pageid=index&extend=call_share
	
2、拨打电话方法

	例：DomobLanding.ext.call.init('18090591207')
	
	注：该方法需要触发一个事件来引用
	
3、分享微博方法

	例：
	DomobLanding.ext.share.init({title:'',url:'',pic:''}).tencent(); 腾讯
	DomobLanding.ext.share.init({title:'',url:'',pic:''}).douban(); 豆瓣
	DomobLanding.ext.share.init({title:'',url:'',pic:''}).qzone(); qq空间
	DomobLanding.ext.share.init({title:'',url:'',pic:''}).kaixin(); 开心
	DomobLanding.ext.share.init({title:'',url:'',pic:''}).renren(); 人人	
	
	注：该方法需要触发一个事件来引用

4、点击监测方法

	DomobLanding.monitor.clk("tijiao");
	
	注：该方法需要触发一个事件来引用
	
5、收集注册数据方法

	1、正常情况下：
		DomobLanding.monitor.reg({
			username:_username.value,
			mobilenumber:_mobilenumber.value
		 });
	 
	2、当一个项目（一个相同的landingid）有2个注册的时候：
		DomobLanding.monitor.reg({
			username:_username.value,
			mobilenumber:_mobilenumber.value
		},'','index');
		DomobLanding.monitor.reg({
			username:_username.value,
			mobilenumber:_mobilenumber.value
		},'','other');
	 
	
	
	
