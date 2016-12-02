<template>
<div class="hb100">
<!-----------------------------head---------------------------->
	<div class="NoalHead clearfloat">
		<div class="logo">
			<img src="../assets/logo.png" />
		</div>
		<div class="right">
			<div class="search">
				<img src="../assets/sousuo.png" />
				<input type="text">
			</div>
			<ul class="list">
				<li><a>您好,超级管理员</a></li>
				<li>|</li>
				<li><a>退出</a></li>
				<li>|</li>
				<li><a><img class="xiaoxi" src="../assets/xiaoxi.png" />4</a></li>
				<li>|</li>
				<li><a @click='toggleshow()'><img class="yifu" src="../assets/yifu.png"/></a></li>
				<!--<li>|</li>-->
				<li class="liwidth" :class='{"bgfff":scshow}' @click='scdivshow()'>
					<a>
						<img class="sc" v-if='scshow' src="../assets/sc-2.png"/>
						<img class="sc" v-else src="../assets/sc-1.png"/>
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
	 		
	 	</div>
	 	<div id="bodyright" class="body-right">
	 		
	 	</div>
	 </div>
<!-----------------------------foot---------------------------->
	 
</div>
</template>

<script>

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
			]
    }
 },
	methods:{
		toggleshow:function(){
			this.themeshow=!this.themeshow;
		},
		scdivshow:function(){
			this.scshow=!this.scshow;
		}
	}
}


</script>

