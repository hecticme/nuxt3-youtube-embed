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

<style scoped>
.youtube-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
  width: 100%;
}

.youtube-title {
  font-size: 2rem;
  font-weight: 700;
}

#youtube-player {
  width: 75%;
  aspect-ratio: 16 / 9;
  border-radius: 16px;
}
</style>
