<script>
    import Draggable from '$lib/components/Draggable.svelte';

    let products = [
        { title: 'Product', price: 100 },
        { title: 'Product', price: 100 },
        { title: 'Product', price: 100 },
        { title: 'Product', price: 100 },
        { title: 'Product', price: 100 },
        { title: 'Product', price: 100 },
    ]

    let size = 2;

    function add() {
        products = products.concat({ title: 'New Item', price: 100 });
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
                        <div class="cursor-pointer w-full text-center rounded flex-1 appearance-none  py-2 px-4 bg-white text-neutral-700  text-base peer-checked:outline-none font-medium peer-checked:bg-stone-700 peer-checked:text-stone-100">
                        small
                        </div>
                      </label>
                    
                      <label class="w-1/3">
                        <input class="sr-only peer" name="privacy" type="radio" bind:group={size} value={2} />
                        <div class="cursor-pointer w-full text-center rounded flex-1 appearance-none py-2 px-4 bg-white text-neutral-700  text-base peer-checked:outline-none font-medium peer-checked:bg-stone-700 peer-checked:text-stone-100">
                        medium
                        </div>
                      </label>
                    
                      <label class="w-1/3">
                        <input class="sr-only peer" name="privacy" type="radio" bind:group={size} value={3} />
                        <div class="cursor-pointer w-full text-center rounded flex-1 appearance-none py-2 px-4 bg-white text-neutral-700  text-base peer-checked:outline-none font-medium peer-checked:bg-stone-700 peer-checked:text-stone-100">
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
            <div class="a5 print:border print:border-stone-300 font-suisse w-[130mm] h-[180mm] bg-white p-6 flex flex-col justify-between">
                <div class="head h-1/5">
                    <h1 class="title uppercase text-6xl leading-none"> Le Concept</h1>
                </div>
                <div class="content ">
                    <div class="products mb-4 {size === 1 ? 'text-2xl' : ''} {size === 2 ? 'text-3xl' : ''} {size === 3 ? 'text-4xl' : ''} leading-snug">
                    {#each products as product}
                        <div class="flex w-full justify-between items-end mb-2 last:mb-0">
                            <p class="grow leading-tight" >{product.title}</p>
                            <p class="flex-none leading-tight text-right" >{product.price} Kč</p>
                        </div>
                {/each} 
            </div>
                <div class="foot text-right {size === 1 ? 'text-2xl' : ''} {size === 2 ? 'text-3xl' : ''} {size === 3 ? 'text-4xl' : ''} lowercase leading-none">
                    <p class="">více na leconcept.cz</p>
                </div>
                </div>
                
                

            </div>
        </div>
    
</div>
