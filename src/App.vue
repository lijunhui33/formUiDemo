<template>
	<div id="app">

		<ml-from :model="userInfo" :rules="rules" ref="clickForm">
			<from-item label="模拟校验,不能为1" prop="name">
				<ml-input v-model="userInfo.name"></ml-input>
			</from-item>
			<from-item label="模拟校验,必须是李四" prop="name2">
				<ml-input v-model="userInfo.name2"></ml-input>
			</from-item>
			<button @click="clicks">提交</button>
		</ml-from>
	</div>
</template>

<script>
	import mlInput from './components/mlInput.vue'
	import fromItem from './components/fromItem.vue'
	import mlFrom from './components/from.vue'
	export default {
		
		name: 'app',
		components: {
			mlInput,
			fromItem,
			mlFrom
		},
		data() {
			return {
				userInfo: {
					name: '',
					name2: '李四'
				},
				rules: {
					name: [{
						requured: true,
						message: '不能为1'
					}],
					name2: [{
						requured: true,
						message: '没填成李四'
					}]
				}
			}
		},
		methods:{
			clicks(){
				this.$refs['clickForm'].validate(valid=>{
					console.log(valid)
					if(valid){
						alert('全正确')
					}else{
						alert('有错误的')
					}
				})
			}
		}
	}
</script>

<style>
	#app {
		font-family: 'Avenir', Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
	}
</style>
