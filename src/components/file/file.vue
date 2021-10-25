<template>
  <li>
		<label class="row" :style="getIndent()">
			<input type="radio" name="pressed" class="row-input visually-hidden" @click="changeVisibility"/>
			{{type === 'directory' ? 'directory' : 'file'}} {{fileName}}
			<div class="row-style"></div>
		</label>
		<entity v-if="isShown" :contents="contents" :level="this.$props.level + 1"/>
  </li>
</template>

<script>

export default {
  name: 'file',
	components: {
		entity: () => import('../entity/entity.vue'),
	},
	data: function() {
		return {
			isShown: false,
		}
	},
	methods: {
		changeVisibility() {
			this.isShown = !this.isShown;
		},
		getIndent() {
			console.log(1)
			return `padding-left: ${20 * this.$props.level}px`
		},
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
	.row {
		display: flex;
		/* padding-left: 2px; */
		align-items: center;
		position: relative;
		width: 100%;
		height: 25px;

		cursor: pointer;
	}

	.row-style {
		position: absolute;
		left: 0;
		top: 0;
		right: 0;
		bottom: 0;
		z-index: -1;
	}

	.row-input:checked + .row-style {
		background-color: #cce8ff;
		border: 1px solid #99d1ff;
	}

</style>

