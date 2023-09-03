<script>



    let measurment = "miles";

    let runType = "ob"

    const toggleMeasurment = () => {
        if(measurment === "miles"){
            measurment = "km";
        } else measurment = "miles";
    }
    
    const toggleType = (button) => {
        if(runType === "ob"){
            runType = "loop";
            document.getElementById("loop-btn").dataset.selected = "true";
            document.getElementById("o&b-btn").dataset.selected = "false";
        } else {
            runType = "ob";
            document.getElementById("loop-btn").dataset.selected = "false";
            document.getElementById("o&b-btn").dataset.selected = "true";
        }
        
    
    }

</script>


<div class="bg-blue-400 w-screen h-screen pt-4 pr-4">

    <div class=" bg-white mr-4 ml-4 p-4 grid grid-cols-8 grid-rows-5 gap-x-4 gap-y-2">
        
        <!-- search bar header -->
        <div class="row-span-1 col-span-3 text-lg">
            <p>Starting Address</p>
        </div>

        <!-- address search bar -->
        <div class="row-start-2 row-end-3 col-span-3">
            <input type="text" class="border-2 border-gray-400 rounded-md w-full hover:border-gray-500 transition ease-in-out bg-gray-100 text-black placeholder:text-gray-500 hover:drop-shadow-md" placeholder="Starting Address">
        </div>

        <!-- my location button -->
        <div class="row-start-2 row-end-3 col-start-4 col-end-5">
            <button class="bg-zinc-500 border-2 rounded-md m-0 h-7 p-0.5 hover:drop-shadow-md transition ease-in-out">
                <img src="./my_location.svg" alt="My Location" class=" h-full">
            </button>
        </div>

        <!-- distance header -->
        <div class="row-start-3 row-end-4 col-span-1 flex">
            <p class="self-end">Distance</p>
        </div>

        <!-- distance input -->
        <div class="row-start-4 row-end-5 col-span-1">
            <input type="number" class="border-2 border-gray-400 rounded-md w-full hover:border-gray-500 transition ease-in-out bg-gray-100 text-black placeholder:text-gray-500 hover:drop-shadow-md" value="3">
        </div>

        <!-- distance measurment selector -->
        <div class="row-start-4 row-end-5 col-start-2 col-end-3">
            <!-- svelte-ignore a11y-no-noninteractive-element-interactions -->
            <!-- svelte-ignore a11y-click-events-have-key-events -->
            <p class="hover:text-neutral-500 transition ease-in-out hover:cursor-pointer font-medium w-fit p-1" on:click={toggleMeasurment}>{measurment}</p>

        </div>

        <!-- route type header -->

        <div class="row-start-3 row-end-4 col-start-3 col-end-4 flex">

            <p class="self-end">Route Type</p>

        </div>

        <!-- route type selector loop -->

        <div class="row-start-4 row-end-5 col-start-3 col-end-4 flex gap-3">

            <button data-selected="true" class="data-[selected=true]:bg-zinc-500 border-2 rounded-md p-0.5 data-[selected=true]:text-neutral-800 transition ease-in-out data-[selected=true]:border-neutral-800 bg-zinc-400 text-neutral-600 border-neutral-800 hover:drop-shadow-md" on:click={toggleType} id="loop-btn">
                Loop
            </button>

            <button data-selected="false" class="data-[selected=true]:bg-zinc-500 border-2 rounded-md p-0.5 data-[selected=true]:text-neutral-800 transition ease-in-out data-[selected=true]:border-neutral-800 bg-zinc-400 text-neutral-700 border-neutral-700 hover:drop-shadow-md" on:click={toggleType} id="o&b-btn">
                O&B
            </button>

            
            
        </div>

        

    </div>

</div>
