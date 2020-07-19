<template>
	<div>
		<input type="text" :value="value" @input="onInput">
	</div>
</template>

<script>
	export default{
		props:{
			value:{
				type:String,
				default:''
			}
		},
		methods:{
			onInput(e){
				this.$emit('input',e.target.value)
				this.$parent.$emit('validate')//派发事件给夫元素
			}
		}
	}
</script>

<style>
</style>
