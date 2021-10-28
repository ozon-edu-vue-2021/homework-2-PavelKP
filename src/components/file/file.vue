<template>
  <li>
    <label class="row" :style="cssVars">
      <icon :iconType="iconType" />
      <input
        type="radio"
        name="pressed"
        class="row-input visually-hidden"
        @click="onClick"
        @keydown.prevent
      />
      <a :href="$props.target">{{ fileName }} </a>
      <div class="row-style"></div>
    </label>
    <entity v-if="isShown" :contents="contents" :level="$props.level + 1" />
  </li>
</template>

<script>
import icon from "../icon/icon.vue";

export default {
  name: "file",
  components: {
    entity: () => import("../entity/entity.vue"),
    icon,
  },
	inject: ['reactive'],
  data() {
    return {
      isShown: false,
    };
  },
  methods: {
    onClick() {
      this.isShown = !this.isShown;
			this.reactive.absolutePath = this.$props.fileName;
    },
  },
  computed: {
    cssVars() {
      return {
        "--indent-multiplier": this.$props.level,
      };
    },
		iconType() {
      if (this.$props.type === "directory" && !this.isShown) {
        return "folder";
      } else if (this.$props.type === "directory" && this.isShown) {
        return "folder-opened";
      } else if (this.$props.type === "file") {
        return "file";
      } else if (this.$props.type === "link") {
        return "link";
      }
			return 'file'
    },
  },
  props: {
    fileName: String,
    level: Number,
    contents: Array,
    type: String,
    target: String,
  },
};
</script>

<style scoped>
.row {
  display: flex;
	padding-left: calc(20px * var(--indent-multiplier));
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
.row:hover .row-style {
  background-color: #e5f3ff;
}
.row-input:checked ~ .row-style {
  background-color: #cce8ff;
  border: 1px solid #99d1ff;
}
</style>

