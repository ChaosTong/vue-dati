<template>
	<div class="score">
    <div class="your_scores_container">
		   <header >
        <span class="yourchengji">您的成绩</span>
				<div class="your_scores"><span class="score_num">{{score}}</span><span class="fenshu">分！</span></div>
        <div class="timeCost">答题时间：<span>{{totalTime}}</span>s</div>
		   </header>
		   <div class="result_comment">{{comment}}</div>
		</div>
    <br>
		<div>
      <p class="comment">
        作者说明：
        最后有点写不下去了，思维有点混乱，很多事情也记不太清了。
测试结果/选项/打分可能有欠妥的地方，请不要过度在意结果，就是图一乐。

主要目的呢，是从我的角度和信息分析一下👸到底是个什么样的人。之前有看法认为👸没心机，我是不太赞同的。

有没有心机，跟他对你有没有图谋是两回事，跟他把不把你当傻逼当工具也是两回事。

你要说他不通人情世故，放在十几个月前可能确实比很多人差，但是人类模仿的能力连婴儿都有。

你看多了卖惨，你自然就学会了卖惨。
你看到别人装傻得到了好处，你下次也会试着装一下的。
你第一次成功骗到了傻帽，之后你觉得所有人都长得像傻帽。
你身边都是称兄道弟的人，你也跟别人兄弟相称。
有人踩着兄弟上位，你也在找你脚边有没有合适的。
你身边都是白嫖怪，你也会白嫖你认识的人。
权力使人膨胀，也会使你暴露本性。
你第一次看别人掉坑里，偶然捡到了他掉的钱，下一次没准你都会挖坑了。

当傻帽不是什么好体验，我掉的坑你们记得绕过去。
      </p>
    </div>
	</div>
</template>

<script>
import {mapState,mapActions} from 'vuex'
export default {
  data () {
    return {
    	score:0,
    	showOrhidden:false,
		comment:'',
    commentArr:["👸潜入了纯爱群！ 快跑！ 跑！  ⻊  ",
    "你就是卧底二🐶 请自觉找到二狗并将他禁言时长+1", 
    "你已被👸病毒严重感染，请马上联系老表派出🚑送医",
    " 你有轻微👸病倾向，请近期多🐗接触，远离秃头👨‍",
    "你是一名合格的纯爱战🐺。请联系群主领取🐺资格证，凭此证可联系作者领取车牌一套（误）"]
    }
  },
  computed:mapState(['answerid','totalTime']),
  created(){
  	// 评分
  	this.scoring();
  	// 评论
  	this.scoreComment();
  },
  methods:{
  	...mapActions([
  		'initializeData'
  		]),
  	goHome(){
  	this.$router.push('home');
  },
  scoring(){
    this.answerid.forEach((item,index)=>{
      this.score += item
    })
  },
  scoreComment(){
  		if (this.score<=9) {
  			this.comment=this.commentArr[4];
  			return;
  		}if (this.score<=76) {
  			this.comment=this.commentArr[3];
  			return;
  		}if (this.score<=59) {
  			this.comment=this.commentArr[2];
  			return;
  		}if (this.score<=36) {
  			this.comment=this.commentArr[1];
  			return;
  		}if (this.score>76) {
  			this.comment=this.commentArr[0];
  		}
  },
  showCover(){
  	this.showOrhidden=!this.showOrhidden;
  },
}
}
</script>

<style scoped>
.score{
  height: 6.67rem; 
  /* background: url('../../assets/xiaoxin08.jpg') no-repeat; */
  background-size: 100%;
  width: 100%;
  padding-top: 0.2rem;
}
/*得分*/
.your_scores_container{
  position: relative;
  width: 2.27rem;
  height: 1.5rem;
  border-radius: 0.1rem;
  margin: 0 auto;
  text-align: center;
  background-color: white;
}
.your_scores{
  width: 100%;
  font-size: 0.3rem;
  font-weight: 900;
  text-indent: 0.2rem;
  position: absolute;
  top: 0.38rem;
}
.score_num{
  font-family: Tahoma,Helvetica,Arial;
  color: #A51D31;
}
.fenshu{
  color: #A51D31;
}
.yourchengji{
  display: block;
  font-size: 0.2rem;
  font-weight: 800;
  padding-top: 0.1rem;
}
.result_comment{
  margin-top: 0.08rem;
  padding: 0 0.06rem;
  font-size: 0.15rem;
  font-weight: 800;
}
.comment{
  margin-top: 0.08rem;
  padding: 0 0.06rem;
  font-size: 0.15rem;
  font-weight: 800;
}
/*用时*/
.timeCost{
  margin-top: 0.5rem;
  font-weight: 800;
  font-size: .16rem;
}
/*分享*/
.isShow{
  height: 6.67rem;
  width: 100%;
  /* background: url('../../assets/xiaoxin07.jpg'); */
  background-size: 100% 100%;
  opacity: .9;
  position: absolute;
  top: 0;
  left: 0;
  
}
.thxShare{
  font-size: 0.3rem;
  display: block;
  color: white;
  /*text-align: center;*/
  margin-top: 1.5rem;
  width: 1.6rem;
  height: 0.44rem;
  background-color: #DF3D42;
  border-radius: 0.2rem;
  float: right;
  padding-left: 0.1rem;
}
/*回到主页*/
.gohome{
  font-size: .16rem;
  display: block;
  height: 0.35rem;
  width: 0.8rem;
  line-height: 0.35rem;
  border-radius: 0.1rem;
  color: white;
  background-color: skyblue;
  background-size: 100% 100%;
  position: absolute;
  top: 3.3rem;
  left: 20%;
  background-repeat: no-repeat;
  text-align: center;
}
/*点击分享*/
.clickShare{
  font-size: .16rem;
  display: block;
  height: 0.35rem;
  width: 0.8rem;
  line-height: 0.35rem;
  border-radius: 0.1rem;
  color: white;
  background-color: skyblue;
  background-size: 100% 100%;
  position: absolute;
  top: 3.6rem;
  left: 72%;
  background-repeat: no-repeat;
  text-align: center;
}

</style>
