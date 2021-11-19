<template>
    <button :class="btnClass" :style="btnStyle">
        <slot name="left"></slot>
        <span><slot></slot></span>
        <slot name="right"></slot>
    </button>
</template>

<script lang="ts" setup>
import { computed, defineProps } from "vue";

const props = defineProps({
    bg: {
        type: String,
        default: "#f7f7f7",
    },
    color: {
        type: String,
        default: "#606266",
    },
});

const btnClass = computed(() => {
    return {
        "el-btn": true,
    };
});

const btnStyle = computed(() => {
    return {
        background: props.bg,
    };
});
</script>

<style lang="scss">
.el-btn {
    padding: 8px 16px;
    color: #ffffff;
    line-height: 1;
    outline: none;
    border: none;
    border-radius: 4px;
    cursor: pointer;
    transition: all 0.2s;
    position: relative;
    user-select: none;

    &::after {
        content: "";
        position: absolute;
        z-index: -1;
        background: inherit;
        width: 100%;
        height: 100%;
        top: 2px;
        left: 2px;
        filter: blur(3px);
    }
}
</style>
