<template>
	<div @click="changeCode">
		<verifyCode :identifyCode="identifyCode"></verifyCode>
	</div>
</template>

<script>
/* eslint-disable */
import verifyCode from "@/components/VerifyCode";
export default {
  	name: 'HelloWorld',
	components:{verifyCode},
  	data(){
		return{
			identifyCode:'',
			identifyCodes:'abcdefghijklmnopqrstuvwxyz0123456789'
		}
	},
	methods:{
		randomNum(min,max){
			max = max + 1
			return Math.floor(Math.random()*((max-min)+min))
		},
		makeCode(data,len){
			for(let i = 0;i<len;i++){
				this.identifyCode += data[this.randomNum(0,data.length-1)]
			}
		},
		changeCode(){
			this.identifyCode = ''
			this.makeCode(this.identifyCodes,4)
		}
	},
	mounted() {
		this.identifyCode=''//初始化验证码
		this.makeCode(this.identifyCodes,4)
	},
	watch:{
		identifyCode(){
			console.log(this.identifyCode)
		}
	}

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
