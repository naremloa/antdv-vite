<script setup lang="ts">
import { AdminButton as Button } from "./components/button";
import { AdminInput as Input } from "./components/input";

type a = typeof Input;
</script>

<template>
  <Input :addon-before="'前面內容'">
    <template #addonAfter>
      <span>後面內容</span>
    </template>
  </Input>
</template>
