<template>
<div class="hb100">
<!-----------------------------head---------------------------->
	<div class="NoalHead clearfloat">
		<div class="logo">
			<img src="../../static/images/logo.png" />
		</div>
		<div class="right">
			<div class="search">
				<img src="../../static/images/sousuo.png" />
				<input type="text">
			</div>
			<ul class="list">
				<li><a>您好,超级管理员</a></li>
				<li>|</li>
				<li><a>退出</a></li>
				<li>|</li>
				<li><a><img class="xiaoxi" src="../../static/images/xiaoxi.png" />4</a></li>
				<li>|</li>
				<li><a @click='toggleshow()'><img class="yifu" src="../../static/images/yifu.png"/></a></li>
				<!--<li>|</li>-->
				<li class="liwidth" :class='{"bgfff":scshow}' @click='scdivshow()'>
					<a>
						<img class="sc" v-if='scshow' src="../../static/images/sc-2.png"/>
						<img class="sc" v-else src="../../static/images/sc-1.png"/>
					</a>
				</li>
			</ul>
		</div>
		<div class="theme" v-show='themeshow'>
			<div class="hd">主题切换</div>
			<ul>
				<li v-for='theme in themes'>{{theme.text}}</li>
			</ul>
		</div>
		<div class="scdiv" v-show='scshow'>
			<h4 class="hd">收藏夹</h4>
			<ul>
				<li>点击删除全部</li>
				<li v-for='sc in scs'>{{sc.text}}</li>
			</ul>
		</div>
	</div>
<!-----------------------------body---------------------------->
	 <div id='NoalBody' class="NoalBody clearfloat">
	 	<div class="body-left">
	 		<div class="hd">首页</div>
	 		<ul v-for="list in lists">
	 			<li>{{list.text}}</li>
	 		</ul>
	 	</div>
	 	<div id="bodyright">
	 		<div class="body-right">
	 			<ul>
	 				<li v-for="menu in menus" @click="liclick(menu)"><img v-bind:src="menu.src"><p>{{menu.text}}</p></li>
	 			</ul>
	 		</div>
	 		
	 	</div>
	 </div>
<!-----------------------------foot---------------------------->
	<div class="foot">
		<div class="hd">
			<span class="window"><img src="../../static/images/window.png"></span>
			<ul class="navul">
				<li v-for="(navlist,index) in navlists" :class="{'blue':navlist.bg}" @click="navliclick(navlist)">{{navlist.text}}<img @click="closeclick(index)" src="../../static/images/close.png"></li>
			</ul>
			<img class="menu" src="../../static/images/lists.png" />
			<ul class="menuul">
				<li @click="closeall()">点击关闭全部</li>
				<li @click="closeother()">点击关闭其他</li>
				<li v-for="(menulist,index) in menulists">{{menulist.text}}<img @click="menucloseclick(index)" src="../../static/images/close.png"></li>
			</ul>
		</div>
	</div>
	 
</div>
</template>

<script>
var winheight=$(window).height();
var winwidth=$(window).width();
var top=parseInt($('.foot').css('top'));
$(function(){
	$('.foot').height(winheight).css('bottom',-(winheight-35));
	$('#NoalBody').height(winheight-85);
	$('.foot .hd .navul').width(winwidth-100);
	$('.window').click(function(){
		animateif();
	})
});

export default {
  name: 'NoalPage',
  data () {
    return {
    	themeshow:false,
    	scshow:false,
        themes:[
				{text:'传统版'},
				{text:'经典版'},
				{text:'个性版'}
		],
		scs:[
				{text:'我的事务工作台'},
				{text:'通讯录'},
				{text:'我的操作日志'},
				{text:'规章制度'}
		],
		lists:[
				{text:'基础平台'},
				{text:'EOC'},
				{text:'数据收集'},
				{text:'我的中心'},
				{text:'报表发布'},
				{text:'WES'},
				{text:'报表中心'}
		],
		menus:[
				{src:'../../static/images/menus/report.png',text:'report',bg:false},
				{src:'../../static/images/menus/report1.png',text:'report1',bg:false},
				{src:'../../static/images/menus/report2.png',text:'report2',bg:false},
				{src:'../../static/images/menus/report3.png',text:'report3',bg:false},
				{src:'../../static/images/menus/report4.png',text:'report4',bg:false},
				{src:'../../static/images/menus/report5.png',text:'report5',bg:false},
				{src:'../../static/images/menus/report6.png',text:'report6',bg:false},
				{src:'../../static/images/menus/report7.png',text:'report7',bg:false},
				{src:'../../static/images/menus/report8.png',text:'report8',bg:false},
				{src:'../../static/images/menus/report9.png',text:'report9',bg:false}
		],
		navlists:[
		{text:"were1"},
		{text:"were2"},
		{text:"were1"},
		{text:"were1"},
		{text:"were1"},
		{text:"were1"},
		{text:"were1"}
			
		],
		menulists:[
		{text:"were"}
		]
    }
 },
	methods:{
		toggleshow:function(){
			this.themeshow=!this.themeshow;
		},
		scdivshow:function(){
			this.scshow=!this.scshow;
		},
		liclick:function(menu){
			var textmenu=menu.text;
			animatetop();
//			数组去重
			var flag=false;
			for (var i=0;i<this.navlists.length;i++) {
				this.navlists[i].bg=false;
				if(textmenu==this.navlists[i].text){
					flag=true;
					this.navlists[i].bg=true;
				}
			}
			if(!flag){
				this.navlists.push({text:textmenu,bg:true});
			}
			if(this.navlists.length>8){
				var menutext=this.navlists[0].text;
				this.navlists.shift();
				this.menulists.push({text:menutext});
			}
			
		},
		closeclick:function(index){
			this.navlists.splice(index,1);
			var flag = false;
			for (var i=0;i<this.navlists.length;i++) {
				if(this.navlists[i].bg){
					flag =true;
				}
			}
			if(this.navlists.length<8){
				if(this.menulists.length>0){
					var navlisttext=this.menulists[0].text;
					this.menulists.shift();
					this.navlists.push({text:navlisttext,bg:false});
				}
			}
			if(!flag){
				if(this.navlists.length-1>=0){
					this.navlists[this.navlists.length-1].bg=true;
				}
			}
			if(this.navlists.length==0){
				animatebottom();
			}
			
			stopBubble();
		},
		navliclick:function(navlist){
			for(var i=0;i<this.navlists.length;i++){
				this.navlists[i].bg=false;
			}
			navlist.bg=true;
			animatetop();
		},
		menucloseclick:function(index){
			this.menulists.splice(index,1);
		},
		closeall:function(){
			this.navlists.splice(0,this.navlists.length);
			this.menulists.splice(0,this.menulists.length);
			animatebottom();
		},
		closeother:function(){
			this.menulists.splice(0,this.menulists.length);
			for (var i=0; i<this.navlists.length;i++) {
				if(this.navlists[i].bg){
					this.navlists[0]=this.navlists[i];
					this.navlists.splice(1,this.navlists.length-1);
				}
			}
		}
	}
}
//判断条件滑动
function animateif(){
	var top=parseInt($('.foot').css('top'));
	if(top>0){
		$('.foot').animate({top:'0px'},200);
	}else{
		$('.foot').animate({top:winheight-35},200);
	}
}
//向上滑动
function animatetop(){
	$('.foot').animate({top:'0px'},200);
}
//往下滑动
function animatebottom(){
	$('.foot').animate({top:winheight-35},200);
}
//阻止冒泡
function stopBubble(e) {
    // 如果提供了事件对象，则这是一个非IE浏览器
    if ( e && e.stopPropagation ) {
        // 因此它支持W3C的stopPropagation()方法 
        e.stopPropagation();
    } else { 
        // 否则，我们需要使用IE的方式来取消事件冒泡
        window.event.cancelBubble = true;
    }
}

</script>

