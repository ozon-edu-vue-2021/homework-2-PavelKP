<template>
  <div 
		:class="['base-icon', {
			'folder': $props.iconType === 'folder',
			'folder-opened': $props.iconType === 'folder-opened',
			'link': $props.iconType === 'link',
			'file': $props.iconType === 'file',
		}]"
	>
  </div>
</template>

<script>

export default {
  name: 'icon',
  props: {
		iconType: {
			type: String,
			required: true,
			default: 'folder',
		}
  }
}
</script>

<style scoped>
	.base-icon {
		width: 24px;
		height: 24px;
		margin-right: 4px;

		background-repeat: no-repeat;
    background-position: center;
	}
	.folder {
		background-image: url('~@/assets/folder.svg');
	}
	.folder-opened {
		background-image: url('~@/assets/folder-opened.svg');
	}
	.file {
		background-image: url('~@/assets/file.svg');
	}
	.link {
		background-image: url('~@/assets/link.svg');
	}
</style>

