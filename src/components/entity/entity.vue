<template>
	<ul class="list">
		<file
			v-for="item in contents" 
			:key="item.name" 
			:fileName="item.name"
			:contents="item.contents"
			:type="item.type"
			:target="item.target"
			:level="level"
		/>
	</ul>
</template>

<script>
import file from '../file/file.vue';

export default {
  name: 'entity',
	components: {
		file,
	},
  props: {
		level: Number,
		contents: Array,
  }
}
</script>

<style scoped>
	.list {
		margin: 0;
    padding: 0;
    list-style: none;
		text-align: left;
	}
</style>

