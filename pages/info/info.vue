<template>
	<view class="container">
		<view class="list">
			<view class="list-item"><navigator url="../index/index">文章详情</navigator></view>
			<view class="list-item"><text>第一篇文章</text></view>
			雨来得那么及时，那么温润，那么调皮。风极为温柔，清风入弦，落叶旋转起舞，荣枯有序，一盆菊，暗香浮动，盈香满袖，捡拾一枚落叶，静坐秋的丰盈来感受秋的静美，我于秋写意秋风秋雨，等待收获丰盈……',			
			<view class="list-item">
				<button type="primary" @tap="logout">退出</button>
			</view>
		</view>
	</view>
</template>

<script>
	var loginRes, _self;
	export default {
		data() {
			return {
				storageData: {},
				messages:10,
				followed:5,
				notices:66,
				scores:100,
				articles:[{
					id:1,
					title:'第一篇文章',
					content:'雨来得那么及时，那么温润，那么调皮。风极为温柔，清风入弦，落叶旋转起舞，荣枯有序，一盆菊，暗香浮动，盈香满袖，捡拾一枚落叶，静坐秋的丰盈来感受秋的静美，我于秋写意秋风秋雨，等待收获丰盈……',
					icon1:'../../static/commentflashnews.png',
					icon2:'../../static/like1.png',
					time:'刚刚'
				},
				{
					id:2,
					title:'第二篇文章',
					content:'莲，通过看别人的历史,可以折射出自己的未来,莫名的感慨,有一种享受,随笔六则,意境,人生的限度,深蓝,生死以外无大事,能开心的生活已经很满足了,生而孤独——世俗篇,心灵与气质',
					icon1:'../../static/commentflashnews.png',
					icon2:'../../static/like1.png',
					time:'1分钟前'
				},
				{
					id:3,
					title:'第三篇文章',
					content:'如果有人要跟你分手，永远别去问分手的理由。有些人会来，有些人会走，找的理由都不同，但真正原因都一样。来是爱，走是不爱，并不会有其他特别的。爱你时，能忍你的刁蛮任性。不爱你时，连一句话说错都忍不了。世上最温暖的是爱，最冰凉的是不爱，仅此而已。',
					icon1:'../../static/commentflashnews.png',
					icon2:'../../static/like1.png',
					time:'1天前'
				},
				{
					id:4,
					title:'第四篇文章',
					content:'当她不爱你的时候，也一定要祝福她。有了爱，便不该有恨，因为曾经有爱，有爱的日子里是快乐的，有缘在一起也是快乐，有过快乐有过爱，就不会再有恨。她失去的是一个爱她的人，而你失去了一个不爱你的人，却得到了一个重新生活、重新去爱的机会。请你深深呼吸，一生的路上，铺满了爱的花蕾，总有那么一朵属于你，花儿虽多，却没有重复的一朵，这是生生世世早已经注定的。',
					icon1:'../../static/commentflashnews.png',
					icon2:'../../static/like1.png',
					time:'一周前'
				},
				{
					id:5,
					title:'第五篇文章',
					content:'经典语句：缘是一种自然而神秘的心灵力量小时候不会做人，而尽享了做人的快乐珍惜每一个平凡而美好的今天转瞬即逝的，不仅仅是爱情兴之所至，心之所安我心眼有点小，但是不缺。别再为错过了什么而懊悔学会宽待自己是一件非常重要的事情男女搭配，干活不累最好的，不一定是最合适的；最合适的，才是真正最好的所有的悲伤，总会留下一丝欢乐的线索如果有来生，要做一棵树，站成永恒',
					icon1:'../../static/commentflashnews.png',
					icon2:'../../static/like1.png',
					time:'两天前'
				}
				]
			};
		},
		onLoad: function() {
			
		},
		onShow: function() {
			var _this=this;
			const loginKey = uni.getStorageSync('login_key');
			console.log("come");
			if (loginKey) {
				console.log(loginKey);
				this.storageData = {
					login: loginKey.login,
					nickname: loginKey.nickname,
					avatar: loginKey.avatar,
				};
				
			}else{
				this.storageData ={
					login: false
				}
			};
			uni.request({
				url: 'http://localhost:8080/api/user/avatar/' + uni.getStorageSync('login_key').userId,
				method: 'GET',
				header: { 'content-type': 'application/json' },
				success: res => {
					if (res.data.code === 0) {
						console.log(res.data.data);
						_this.avatar = res.data.data.avatar;
						_this.nickname = res.data.data.nickname;
					}
				}
			});
		},
		methods: {
			
		}
	};
</script>

<style>
</style>
