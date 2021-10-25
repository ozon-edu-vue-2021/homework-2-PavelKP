<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
		<entity 
			:contents="this.$options.firstLevel"
			:level="0"
		/>
  </div>
</template>

<script>
import structure from '../public/static/node_modules.json'
import entity from './components/entity/entity.vue';

export default {
  name: 'App',
  components: {
    entity
  },
	created() {
		this.$options.firstLevel = [structure];
	},
	mounted() {
		const test = structure.contents[0].contents[0];
		console.log(test);
		// this.openFolder([test]); // [structure]
	},
	methods: {
		openFolder(item, level=0) {
			item.forEach((innerItem) => {
				if (innerItem.type === 'directory') {
					console.log('--'.repeat(level) + innerItem.name);
					this.openFolder(innerItem.contents, level+1);
				} else {
					console.log('--'.repeat(level) + innerItem.name);
				}
			})
		}
	}
}
</script>

<style>
	#app {
		font-family: Avenir, Helvetica, Arial, sans-serif;
		-webkit-font-smoothing: antialiased;
		-moz-osx-font-smoothing: grayscale;
		text-align: center;
		color: #2c3e50;
		margin-top: 60px;
		box-sizing: border-box;
	}

	.visually-hidden {
		position: absolute !important;
		clip: rect(1px 1px 1px 1px); /* IE6, IE7 */
		clip: rect(1px, 1px, 1px, 1px);
		padding:0 !important;
		border:0 !important;
		height: 1px !important; 
		width: 1px !important; 
		overflow: hidden;
	}
</style>
