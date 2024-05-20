<script>
    import { slide } from "svelte/transition";

    let photos = [
      './carousel/1.jpg',
      'https://via.placeholder.com/600',
      'https://via.placeholder.com/600',
      'https://via.placeholder.com/600',
      'https://via.placeholder.com/600',
      'https://via.placeholder.com/600',
      'https://via.placeholder.com/600',
      'https://via.placeholder.com/600',
      'https://via.placeholder.com/600',
      'https://via.placeholder.com/600',
      'https://via.placeholder.com/600',
      'https://via.placeholder.com/600',
      'https://via.placeholder.com/600',
      'https://via.placeholder.com/600',
    ];
  </script>
  
<div class="max-w-screen-lg mx-auto p-4">
    <div class="grid grid-cols-2 md:grid-cols-4 lg:grid-cols-4 gap-4">
        {#each photos.slice(0, 12) as photo}
        <div class="relative w-full photo">
          <img src={photo} alt={photo} class="object-cover h-full rounded-lg cursor-pointer" />
          <div class="absolute bottom-0 w-full bg-white bg-opacity-80 text-center p-2">
            말티즈 분양
          </div>
        </div>
        {/each}
    </div>
</div>

<style>
.photo:hover {
    transform: scale(1.05); /* 마우스를 올렸을 때 약간 확대됨 */
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.3); /* 그림자 효과 추가 */
}
</style>