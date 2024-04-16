<script setup lang="ts">
useHead({
  script: [
    {
      src: 'https://www.youtube.com/iframe_api',
    },
  ],
})

const videoTitle = ref('Vapor Trail')

onMounted(() => {
  function onYouTubeIframeAPIReady () {
    // TODO: Declare type for "YT" object.
    // @ts-expect-error
    const player = new YT.Player('youtube-player', {
      type: 'text/html',
      events: {
        onReady: () => {
          console.log('Ready!')
        },
        onStateChange: () => {
          console.log('Something changed.')
        },
      },
    })

    return player
  }

  onYouTubeIframeAPIReady()
})
</script>

<template>
  <section class="youtube-wrapper">
    <h1 class="youtube-title">
      {{ videoTitle }}
    </h1>

    <iframe
      id="youtube-player"
      allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share"
      allowfullscreen
      referrerpolicy="strict-origin-when-cross-origin"
      src="https://www.youtube.com/embed/24g3l_IJuIE?enablejsapi=1"
      :title="videoTitle"
    />
  </section>
</template>
