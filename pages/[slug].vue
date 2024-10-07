<script setup>
  const { $directus, $readItem, $readItems } = useNuxtApp()
  const route = useRoute()

  const { data: page } = await useAsyncData('page', () => {
    return $directus.request($readItem('pages', route.params.slug))
  })

  if(!page.value) throw createError({
    statusCode: 404,
    statusMessage: 'Page Not Found'
  })
</script>

<template>
  <div class='page'>
    <div class='page-container'>

    </div>
  </div>
</template>