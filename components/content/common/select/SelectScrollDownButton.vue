<template>
  <SelectScrollDownButton
    data-slot="select-scroll-down-button"
    v-bind="forwardedProps"
    :class="cn('flex cursor-default items-center justify-center py-1', props.class)"
  >
    <slot>
      <Icon
        name="lucide:chevron-down"
        class="size-4 opacity-50"
      />
    </slot>
  </SelectScrollDownButton>
</template>

<script setup lang="ts">
import { cn } from "@/lib/utils";
import { SelectScrollDownButton, type SelectScrollDownButtonProps, useForwardProps } from "reka-ui";
import { computed, type HTMLAttributes } from "vue";

const props = defineProps<SelectScrollDownButtonProps & { class?: HTMLAttributes["class"] }>();

const delegatedProps = computed(() => {
  const { class: _, ...delegated } = props;

  return delegated;
});

const forwardedProps = useForwardProps(delegatedProps);
</script>
