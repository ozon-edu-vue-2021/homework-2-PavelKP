<template>
	<div>
		<file
			v-for="item in contents" 
			:key="item.name" 
			:fileName="item.name"
			:contents="item.contents"
			:type="item.type"
		/>
	</div>
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
		indent: String,
		contents: Array,
  }
}
</script>

