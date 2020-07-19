<template>
	<div>
		<label v-if="label!=''">{{label}}</label>
		<slot></slot>
		<!-- 校验信息 -->
		<p v-if="error" style="color: red;">{{error}}</p>
		<!-- 校验规则 -->
		<!-- <p>{{form.rules}}</p> -->
	</div>
</template>

<script>
	export default{
		inject:['form'],
		data(){
			return{
				error:''//error是空说明校验没通过
			}
		},
		props:{
			label:{
				type:String,
				default:''
				
			},
			prop:{
				type:String,
				
			}
		},
		created(){
		},
		mounted(){
			this.$on('validate',()=>{//监听子元素派发的事件
					this.validate()
			})
		},
		methods:{
			validate(){
				//规则
				// console.log(this.form.rules[this.prop])
				const rules = this.form.rules[this.prop]
				//值
				// console.log(this.form.model[this.prop])
				const value = this.form.model[this.prop]
				//校验描述对象
				
				console.log(this.prop)
				if(this.prop === 'name'){
					console.log(value)
					if(value == 1){
						this.error = rules[0].message
						return false
					}else{
						this.error = ''
						return true
					}
				}
				if(this.prop === 'name2'){
					console.log(value)
					if(value != '李四'){
						this.error = rules[0].message
						return false
					}else{
						this.error = ''
						return true
					}
				}
			}
		}
	}
</script>

<style>
</style>
