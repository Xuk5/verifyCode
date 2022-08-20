<template>
	<div>
		<canvas id="canvas" width="contentWidth" height="contentHeight"></canvas>
	</div>
</template>

<script>
export default {
	name:'verifyCode',
	props:{
		identifyCode:{
			type:String,
			default:'1234',
			required:true
		},
		contentWidth: {
			type: Number,
			default: 160
		},
		contentHeight:{
			type:Number,
			default:80
		}
	},
	methods:{
		//生成一个随机数
		randomNum(min,max){
			return Math.floor(Math.random()*((max-min)+min))
		},
		//生成一个随机颜色
		randomColor(min,max){
			let r = this.randomNum(min,max)
			let g = this.randomNum(min,max)
			let b = this.randomNum(min,max)
			return `rgb(${r},${g},${b})`
		},
		//绘图
		drawPic(){
			let canvas = document.getElementById('canvas')
			let ctx = canvas.getContext('2d')
			ctx.fillStyle = this.randomColor(180,255)
			ctx.fillRect(0,0,this.contentWidth,this.contentHeight)

		}
	}
}
</script>