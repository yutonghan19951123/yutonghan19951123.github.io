<script setup lang="ts">
  import { handleLinkClick, getTooltipText } from '~/utils/linkHandlers'

  interface Props {
    link: any
  }

  defineProps<Props>()
</script>

<template>
  <CopyTooltip
    :text="getTooltipText(link)"
    :copy-text="link?.account ?? link.to"
    :aria-label="link['aria-label'] ?? ''"
  >
    <UButton
      v-bind="{
        size: 'xs',
        color: 'neutral',
        variant: 'ghost',
        ...link
      }"
      @click="handleLinkClick(link)"
    />
  </CopyTooltip>
</template>
