<script>
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

    let currentId = 1;
    let slides

    function prev() {
        let move = currentId * 100;
        slides.style.transform = `translateX(100%)`;
        slides.style.transition = "1s";
    }

    function next() {
        let move = currentId * 100;
        slides.style.transform = `translateX(-100%)`;
        slides.style.transition = "1s";
    }
</script>

<div class="fixed h-[300px] bg-gray-200 inset-0 lg:relative lg:h-[700px]">
    <div class="flex justify-center items-center w-full h-full" bind:this={slides}>
        {#each images as {src}}
            <div class="flex w-full h-full bg-red-100">
                <div class={`h-full w-full bg-center bg-cover bg-[url('${src}')] inset-0`}></div>
            </div>
        {/each}
        <!-- <div class="absolute bg-blue-100 inset-0" bind:this={slides}>
            <div class={`h-full w-full bg-center bg-cover bg-[url('${src}')] inset-0`}></div>
        </div> -->
    </div>
</div>
<div class="mt-[230px] lg:m-0" />
<div>
    <button on:click={prev}>prev</button>
    <button on:click={next}>next</button>
</div>