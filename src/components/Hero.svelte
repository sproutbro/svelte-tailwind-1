<script>
  let hero = true
  let playbackRate=0.5
</script>

<div class={hero ? "relative w-full lg:px-20" : "hidden" }>
  <video autoplay muted loop playsinline bind:playbackRate={playbackRate} class="w-full h-full object-cover video-brightness">
      <source src="2795691-sd_426_240_25fps.mp4" type="video/mp4">
      <source src="your-video.webm" type="video/webm">
      <!-- 필요한 경우 추가 포맷을 제공할 수 있습니다. -->
      Your browser does not support the video tag.
  </video>
  <div class="absolute top-0 left-0 right-0 flex justify-center mb-4 opacity-50">
    <button class="bg-white rounded-full p-2" on:click={() => hero = !hero}>
        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6 text-gray-800" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
        </svg>
    </button>
  </div>
</div>

<style>
.video-brightness {
  filter: brightness(50%);
}
</style>