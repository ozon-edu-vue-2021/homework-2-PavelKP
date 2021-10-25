<template>
	<ul class="list">
		<file
			v-for="item in contents" 
			:key="item.name" 
			:fileName="item.name"
			:contents="item.contents"
			:type="item.type"
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
    fileName: String,
		level: Number,
		contents: Array,
		type: String,
  }
}
</script>

<style scoped>
	.list {
		margin: 0;
		/* margin-left: 20px; */
    padding: 0;

    list-style: none;
		text-align: left;
	}
</style>

