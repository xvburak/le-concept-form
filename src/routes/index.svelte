<script>
    import Draggable from '$lib/components/Draggable.svelte';

    let products = [{
            title: 'Product',
            price: 100
        },
        {
            title: 'Product',
            price: 100
        },
        {
            title: 'Product',
            price: 100
        },
        {
            title: 'Product',
            price: 100
        },
        {
            title: 'Product',
            price: 100
        },
        {
            title: 'Product',
            price: 100
        },
    ]

    let size = 2;

    function add() {
        products = products.concat({
            title: 'New Item',
            price: 100
        });
    }

    function remove() {
        products = products.slice(0, -1)
    }
</script>


<div class="flex space-x-4 h-full">
    <div class="panel w-[450px] h-screen overflow-y-auto print:hidden">
        <div class="p-2 bg-stone-300">
            <div class="flex space-x-2 mb-2">
                <label class="w-1/3">
                    <input class="sr-only peer" name="privacy" type="radio" bind:group={size} value={1} />
                    <div
                        class="cursor-pointer w-full text-center rounded flex-1 appearance-none  py-2 px-4 bg-white text-neutral-700  text-base peer-checked:outline-none font-medium peer-checked:bg-stone-700 peer-checked:text-stone-100">
                        small
                    </div>
                </label>

                <label class="w-1/3">
                    <input class="sr-only peer" name="privacy" type="radio" bind:group={size} value={2} />
                    <div
                        class="cursor-pointer w-full text-center rounded flex-1 appearance-none py-2 px-4 bg-white text-neutral-700  text-base peer-checked:outline-none font-medium peer-checked:bg-stone-700 peer-checked:text-stone-100">
                        medium
                    </div>
                </label>

                <label class="w-1/3">
                    <input class="sr-only peer" name="privacy" type="radio" bind:group={size} value={3} />
                    <div
                        class="cursor-pointer w-full text-center rounded flex-1 appearance-none py-2 px-4 bg-white text-neutral-700  text-base peer-checked:outline-none font-medium peer-checked:bg-stone-700 peer-checked:text-stone-100">
                        large
                    </div>
                </label>

            </div>

            <div class="mb-2">
                {#each products as product}
                        <div class="flex w-full justify-between space-x-2 mb-2 last:mb-0">
                            <input class="w-3/4 py-2 px-4 rounded" placeholder="Title" bind:value={product.title}>
                            <input class="w-1/4 py-2 px-4 rounded" placeholder="Price" bind:value={product.price}> 
                        </div>
                    {/each} 
                </div>
                <div class="flex space-x-2">
                    <button on:click={() => window.print()} class="bg-white w-1/3 text-purple-500 py-2 font-medium px-4 rounded">
                        print
                    </button>
                    <button on:click={add} class=" bg-white w-1/3 text-green-500 py-2 font-medium px-4 rounded">
                        add
                    </button>
                    <button on:click={remove} class="bg-white w-1/3 text-red-500 py-2 font-medium px-4 rounded">
                        remove
                    </button>
                </div>
                
            </div>
    
    </div>
    <div class="preview w-full h-screen overflow-y-auto p-4 flex justify-center items-center">
            <div class="a5 print:border print:border-stone-300 font-suisse w-[130mm] h-[180mm] bg-white p-[11mm] flex flex-col justify-between">
                <div class="head">
                    <div class="logo w-[65mm]">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 345.68 43.37"><g id="Vrstva_2" data-name="Vrstva 2"><g id="Layer_1" data-name="Layer 1"><path d="M28.14,37v5.61H0V.8H6.57V37Z"/><path d="M61.73.8V6.41H39.36v12H60.53v5.53H39.36V37H61.73v5.61H32.79V.8Z"/><path d="M99,43.37c-12.11,0-19.16-8.9-19.16-21.73C79.85,8.58,87.38.08,99.41.08c9,0,15.79,5.21,17.47,14.35h-6.33c-1.28-5.45-5.29-8.9-11.46-8.9-7.06,0-12.51,5.61-12.51,16.11,0,10.35,5.29,16.28,12.59,16.28,6.17,0,10.26-3.37,11.54-8.9H117C115.28,38.32,108.3,43.37,99,43.37Z"/><path d="M120.65,21.64C120.65,8.9,128.27,0,140.45,0s19.72,8.9,19.72,21.64-7.61,21.73-19.72,21.73S120.65,34.39,120.65,21.64Zm32.79,0c0-10.5-5.69-16.19-13-16.19s-13.07,5.69-13.07,16.19,5.7,16.2,13.07,16.2S153.44,32.15,153.44,21.64Z"/><path d="M171.72,8V42.65h-6.5V.8h9.14L192.8,35.35V.8h6.49V42.65h-9.14Z"/><path d="M223.58,43.37c-12.1,0-19.16-8.9-19.16-21.73C204.42,8.58,212,.08,224,.08c9,0,15.79,5.21,17.47,14.35h-6.33c-1.28-5.45-5.29-8.9-11.47-8.9-7,0-12.5,5.61-12.5,16.11,0,10.35,5.29,16.28,12.58,16.28,6.18,0,10.27-3.37,11.55-8.9h6.33C239.86,38.32,232.88,43.37,223.58,43.37Z"/><path d="M274.81.8V6.41H252.44v12h21.17v5.53H252.44V37h22.37v5.61H245.87V.8Z"/><path d="M311.13,13.63c0,10.5-7.46,12.74-17.56,12.74h-6.89v16.2H280.1V.72h13.47C303.27.8,311.13,2.65,311.13,13.63Zm-24.37,7.21h7.29c5.85,0,10.34-.72,10.34-7.13,0-6.82-4.81-7.54-10.5-7.54h-7.13Z"/><path d="M312.25,6.41V.8h33.43V6.41H332.29V42.65h-6.57V6.41Z"/></g></g></svg>
                    </div>
                </div>
                <div class="content ">
                    <div class="products mb-[9mm]  {size === 1 ? 'text-[19px]' : ''} {size === 2 ? 'text-[27px]' : ''} {size === 3 ? 'text-[35px]' : ''} leading-snug">
                    {#each products as product}
                        <div class="flex w-full justify-between mb-2 last:mb-0">
                            <p class="grow leading-tight" >{product.title}</p>
                            <p class="flex-none leading-tight text-right" >{product.price} Kč</p>
                        </div>
                {/each} 
            </div>
                <div class="foot text-right {size === 1 ? 'text-[19px]' : ''} {size === 2 ? 'text-[27px]' : ''} {size === 3 ? 'text-[35px]' : ''} lowercase leading-none">
                    <p class="">více na leconcept.cz</p>
                </div>
                </div>
                
                

            </div>
        </div>
    
</div>