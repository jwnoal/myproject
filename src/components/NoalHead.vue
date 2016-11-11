<template>
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
    
</template>

<script>
export default {
  name: 'NoalHead',
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

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.NoalHead{width: 100%;height: 50px;background: url(../assets/headbg.jpg) no-repeat;position: relative;}
.logo{width: 200px;height: 100%;line-height: 50px; position: absolute;}
.search{width: 190px;height: 30px;line-height: 30px;background: #f0f8ff;border-radius: 4px;display: inline-block;margin-right: 200px;vertical-align: middle;}
.search img{width: 18px;margin-left: 8px;}
.search input{border: 0;background: none;margin-top: -3px;}
.list{display: inline-block; color: #fff;height: 100%;line-height: 50px;}
.list li{display: inline-block;margin:0 5px;}
.list .liwidth{width: 50px;margin: 0;text-align: center;}
.xiaoxi{width: 16px;}
.yifu{width: 18px;}
.sc{width: 24px;}
.bgfff{background: #fff;}
.theme{width: 95px;text-align: center;position: absolute;top: 50px;right:18px ;background: #f0f8ff;border-radius: 4px;cursor: pointer;}
.theme .hd{line-height: 28px;border-bottom: 1px solid #ddd;}
.theme ul li:hover{background: darkturquoise;}
.scdiv{width: 140px;text-align: left;position: absolute;top: 50px;right:0px ;background: #fff;cursor: pointer;border: 1px solid #ddd;}
.scdiv .hd{line-height: 28px;border-bottom: 1px solid #ddd;padding-left: 10px;}
.scdiv ul li{padding-left: 10px;font-size: 12px;line-height: 24px;}
.scdiv ul li:hover{background: darkturquoise;}
</style>
