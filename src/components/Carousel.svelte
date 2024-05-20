<script>
    import { fade } from "svelte/transition";

    let currentId = 0;
    let intervalTime = 5000;
    let startX = 0;
    let carouseInterval = null;

    let images = [
        {
            "src" : "./carousel/1.jpg"
        },
        {
            "src" : "./carousel/2.jpg"
        },
        {
            "src" : "./carousel/3.jpg"
        },
    ];

    function prev() {
        currentId === 0 ? currentId = images.length - 1 : currentId--
        resetInterval()
    }

    function next() {
        currentId === images.length - 1 ? currentId = 0 : currentId++
        resetInterval()
    }

    function handlePapagination(i) {
        currentId = i
        resetInterval()
    }

    function touchmove(e) {
        let currentX = e.touches[0].clientX
        let diffX = currentX - startX
        
        if(diffX < -50) prev()
        if(diffX > 50) next()
    }

    function touchstart(e) {
        startX = e.touches[0].clientX;
        resetInterval()
    }

    function resetInterval() {
        clearInterval(carouseInterval)
        carouseInterval = setInterval(next, intervalTime)
    }

    carouseInterval = setInterval(next, intervalTime)
</script>
<div class="relative mt-[-72px] lg:mt-[0px]" 
    on:touchstart={touchstart}
    on:touchmove={touchmove}
>
    <div class="relative justify-center w-full bg-gray-200">
        <div class="relative flex items-center overflow-hidden h-[280px] lg:h-[500px]">
            
            {#each images as {src},i}
            {#if currentId === i}
                <img {src} alt="1" in:fade>
                <div class="absolute flex justify-center w-full" in:fade>
                    <div class="w-full max-w-screen-lg text-white p-4">
                        <p class="text-lg">대형견전문 프리미엄샵 큰개닷컴</p>
                        <p class="text-3xl lg:text-5xl">수도권에서 만나는 대형견</p>
                        <button class="bg-transparent border border-white font-semibold mt-2 py-2 px-4 hover:bg-white hover:text-black transition duration-300">
                            바로보기
                        </button>
                    </div>
                </div>
            {/if}
            {/each}
            <div class="papagination flex justify-center">
            {#each images as _,i}
            {#if currentId === i}
                <button class="active" on:click={() => handlePapagination(i)} />            
            {:else}
                <button on:click={() => handlePapagination(i)} />            
            {/if}
            {/each}
            </div>
        </div>
    </div>
</div>

<style>
    .papagination {
        position: absolute;
        bottom: 0;
        padding-bottom: 8px;
        width: 100%;
    }
    .papagination button {
        margin: 0 4px;
        width: 14px;
        height: 14px;
        border: 0;
        border-radius: 50%;
        background-color: rgba(255, 255, 255, 0.8);
        text-align: center;
        cursor: pointer;
    }
    .papagination .active {
        background-color: rgba(255, 0, 0, 0.8);
    }
</style>