<script lang="ts">
export default { name: "AdminInput" };
</script>
<script setup lang="ts">
import { defineProps, withDefaults, defineEmits, toRefs, useSlots } from "vue";
import { AInput } from "./origin";
import type { ChangeEvent } from "./origin";
const props = withDefaults(
  defineProps<{
    addonAfter?: string;
    addonBefore?: string;
    allowClear?: boolean;
    bordered?: boolean;
    disabled?: boolean;
    id?: string;
    maxlength?: number;
  }>(),
  {},
);
const {} = toRefs(props);
const slots = useSlots();

const emit = defineEmits<{
  (e: "onChange", target?: ChangeEvent): void;
}>();
const handleInputEvent = (e?: ChangeEvent) => {
  emit("onChange", e);
};
</script>

<template>
  <div>
    <AInput
      :id="id"
      :addon-after="slots?.addonAfter?.() || addonAfter"
      :addon-before="slots?.addonBefore?.() || addonBefore"
      :allow-clear="allowClear"
      :bordered="bordered"
      :disabled="disabled"
      :maxlength="maxlength"
      @change="handleInputEvent"
    ></AInput>
  </div>
</template>
