<template>
	<div>
		<slot></slot>
	</div>
</template>

<script>
	export default{
		provide(){
			return{
				form:this
			}
		},
		props:{
			model:{
				type:Object,
				required:true
			},
			rules:{
				type:Object,
				
			}
		},
		methods:{
			validate(callBack){
				//获取所以KFormItem
				const tasks = this.$children.map(item=>{
					return item.validate()
				})
				console.log(tasks)
				let type = true 
				tasks.map(item=>{
					if(!item){
						type = false
					}
				})
				callBack(type)
			}
		}
	}
</script>

<style>
</style>
