<script>
    import { page } from '$app/stores';
    import { fade } from 'svelte/transition';
    let backdrop = false;
    $: outerWidth = 0
    $: scrollY = 0
    let nav = true
    let scrollYCopy = 0

    let nav_items = [
        {
            "path": "/",
            "name": "Home"
        },
        {
            "path": "/1",
            "name": "강아지분양"
        },
        {
            "path": "/2",
            "name": "분양후기"
        },
        {
            "path": "/3",
            "name": "분양문의"
        },
        {
            "path": "/4",
            "name": "위치안내"
        },
        {
            "path": "/5",
            "name": "기타견종상식"
        },
    ]

    //스크롤때 실행
    function scroll() {
        // 넓이가 lg 이하일때만 실행
        if(outerWidth < 976) {
            // scroll에 따른 nav toggle
            nav = (scrollYCopy > scrollY) ? true : false
            scrollYCopy = scrollY
        } else {
            nav = true
        }
    }
</script>

<svelte:window bind:scrollY bind:outerWidth on:scroll={scroll}/>
<div class="max-w-screen-lg mx-auto">
    <div class="overflow-hidden h-[72px]">
{#if nav}
    <div class="fixed left-0 z-20 w-full bg-black lg:bg-white bg-opacity-50">
        <nav class="relative max-w-screen-lg mx-auto p-4 flex justify-between items-center z-10">
            <a class="font-bold leading-none z-10" href="/">      
                <p class="font-semibold text-white lg:text-black">
                    Banie<span class="text-indigo-400">susu</span> 
                </p>
            </a>
            <div class="lg:hidden">
                <button on:click={() => backdrop = !backdrop} class="navbar-burger flex items-center text-white p-3">
                    <svg class="block h-4 w-4 fill-current" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
                        <title>Mobile menu</title>
                        <path d="M0 3h20v2H0V3zm0 6h20v2H0V9zm0 6h20v2H0v-2z"></path>
                    </svg>
                </button>
            </div>
            <ul class="hidden absolute top-1/2 left-1/2 transform -translate-y-1/2 -translate-x-1/2 lg:flex lg:justify-center lg:mx-auto lg:items-center lg:pr-20 lg:w-full lg:space-x-6">
                {#each nav_items as nav_item}
                    <li><a class={$page.url.pathname === nav_item.path ? "text-sm text-blue-600 font-bold" : "text-sm text-gray-400 hover:text-gray-500"} href={nav_item.path}>{nav_item.name}</a></li>
                {/each}
            </ul>
            <div class="hidden lg:flex lg:z-10">
                <a class="hidden lg:inline-block lg:ml-auto lg:mr-3 py-2 px-6 bg-gray-50 hover:bg-gray-100 text-sm text-gray-900 font-bold  rounded-xl transition duration-200" href="/signin">Sign In</a>
                <a class="hidden lg:inline-block py-2 px-6 bg-blue-500 hover:bg-blue-600 text-sm text-white font-bold rounded-xl transition duration-200" href="/signup">Sign up</a>
            </div>
        </nav>
    </div>
    <div class={`relative h-[72px] lg:h-[68px]`} />
{/if}
</div>

{#if backdrop}
<div transition:fade class="navbar-menu relative z-50">
    <div class="navbar-backdrop fixed inset-0 bg-gray-800 opacity-25"></div>
    <nav class="fixed top-0 left-0 bottom-0 flex flex-col w-5/6 max-w-sm py-6 px-6 bg-white border-r overflow-y-auto">
        <div class="flex items-center mb-8">
            <a class="mr-auto text-3xl font-bold leading-none" href="/">
                <img src="./logo.png" alt="Logo">
            </a>
            <button on:click={() => backdrop = !backdrop} class="navbar-close">
                <svg class="h-6 w-6 text-gray-400 cursor-pointer hover:text-gray-500" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
                </svg>
            </button>
        </div>
        <div>
            <ul>
                {#each nav_items as nav_item}
                    <li class="mb-1">
                        <a class={$page.url.pathname === nav_item.path ? "block p-4 text-sm font-semibold bg-blue-50 text-blue-600 rounded" : "block p-4 text-sm font-semibold text-gray-400 hover:bg-blue-50 hover:text-blue-600 rounded"} href={nav_item.path}>{nav_item.name}</a>
                    </li>
                {/each}
            </ul>
        </div>
        <div class="mt-auto">
            <div class="pt-6">
                <a class="block px-4 py-3 mb-3 leading-loose text-xs text-center font-semibold leading-none bg-gray-50 hover:bg-gray-100 rounded-xl" href="/signin">Sign in</a>
                <a class="block px-4 py-3 mb-2 leading-loose text-xs text-center text-white font-semibold bg-blue-600 hover:bg-blue-700  rounded-xl" href="/signup">Sign Up</a>
            </div>
            <p class="my-4 text-xs text-center text-gray-400">
                <span>Copyright © 2021</span>
            </p>
        </div>
    </nav>
</div>
{/if}
</div>