<script lang="ts">
export default { name: "AdminButton" };
</script>
<script setup lang="ts">
import { defineProps, withDefaults, defineEmits, toRefs } from "vue";
import { AButton } from "./origin";
import type {
  ButtonType,
  ButtonHTMLType,
  ButtonSize,
  ButtonShape,
} from "./origin";
const props = withDefaults(
  defineProps<{
    block?: boolean;
    danger?: boolean;
    disabled?: boolean;
    ghost?: boolean;
    href?: string;
    htmlType?: ButtonHTMLType;
    loading?: boolean | { delay?: number };
    shape?: ButtonShape;
    size?: ButtonSize;
    target?: string;
    type?: ButtonType;
  }>(),
  {
    block: false,
    danger: false,
    disabled: false,
    ghost: false,
    htmlType: "button",
    loading: false,
    shape: "default",
    size: "middle",
    type: "default",
  },
);
const {} = toRefs(props);

const emit = defineEmits<{
  (e: "onClick", target: MouseEvent): void;
}>();
const handleClickEvent = (e: MouseEvent) => {
  emit("onClick", e);
};
</script>

<template>
  <AButton
    :block="block"
    :danger="danger"
    :disabled="disabled"
    :ghost="ghost"
    :href="href"
    :html-type="htmlType"
    :loading="loading"
    :shape="shape"
    :size="size"
    :target="target"
    :type="type"
    @click.stop="handleClickEvent"
  >
    <slot></slot>
  </AButton>
</template>
