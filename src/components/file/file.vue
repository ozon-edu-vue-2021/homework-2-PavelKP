<template>
  <div>
		<div> {{type === 'directory' ? 'directory' : 'file'}} {{fileName}}</div>
		<entity v-if="type ==='directory'" :contents="contents"/>
  </div>
</template>

<script>

export default {
  name: 'file',
	components: {
		entity: () => import('../entity/entity.vue'),
	},
  props: {
    fileName: String,
		indent: String,
		contents: Array,
		type: String,
  }
}
</script>

