<script setup lang="ts">
const props = withDefaults(
  defineProps<{
    rounded?: 'none' | 'sm' | 'md' | 'lg'
    scrollable?: boolean
  }>(),
  {
    rounded: 'sm',
    scrollable: true,
  },
)
</script>

<template>
  <div class="flex flex-col">
    <div  :class="[
      props.scrollable && 'nui-slimscroll overflow-x-auto',
      props.rounded === 'sm' && 'rounded-md',
      props.rounded === 'md' && 'rounded-lg',
      props.rounded === 'lg' && 'rounded-xl',
    ]">
      <div class="inline-block min-w-full align-middle">
        <div :class="props.scrollable && 'overflow-hidden'">
          <table class="divide-muted-200 bg-[#1E1E1E] dark:divide-muted-700 min-w-full table-fixed divide-y">
            <thead class="border-b border-primary-300/50"
              :class="[
              props.scrollable && 'nui-slimscroll overflow-x-auto',
              props.rounded === 'sm' && 'rounded-md',
              props.rounded === 'md' && 'rounded-lg',
              props.rounded === 'lg' && 'rounded-xl',
            ]">
              <tr>
                <slot name="header" />
              </tr>
            </thead>
            <tbody :class="[
              props.scrollable && 'nui-slimscroll overflow-x-auto',
              props.rounded === 'sm' && 'rounded-md',
              props.rounded === 'md' && 'rounded-lg',
              props.rounded === 'lg' && 'rounded-xl',
            ]" class="divide-muted-200 dark:divide-muted-700 dark:bg-transparent divide-y ">
              <slot />
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>
