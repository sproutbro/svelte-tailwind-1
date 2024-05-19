<script>
    import { fade } from "svelte/transition";

    let currentId = 0;
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
    }

    function next() {
        currentId === images.length - 1 ? currentId = 0 : currentId++
    }
</script>

<div class="fixed top-0 lg:relative">
    <div class="flex justify-center relative w-full bg-gray-200">
        <div class="relative flex items-center overflow-hidden max-h-[50vh]">
            {#each images as {src},i}
            {#if currentId === i}
                <img {src} alt="1" in:fade>
            {/if}
            {/each}
            <div class="papagination flex justify-center">
            {#each images as _,i}
            {#if currentId === i}
                <button class="active" on:click={() => currentId = i} />            
            {:else}
                <button on:click={() => currentId = i} />            
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