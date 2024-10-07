<template>
  <div class="border bg-[#F5FFFB] border-[#77CBF1] my-5 rounded-xl">
    <p class="px-6 py-5 italic text-[15px]">
      <span class="font-bold uppercase">{{ title }} </span>
      {{ content }}
    </p>
  </div>
</template>

<script>
export default {
  name: 'Messages',
  props: {
    title: {
      type: String,
      required: true // this prop is required
    },
    content: {
      type: String,
      default: 'Default content' // default value if no content is provided
    }
  }
}
</script>
