<script>

    // mapbox stuff

    let map;
    let mapContainer;
    let lng, lat, zoom;
    const MAPBOX_TOKEN = "pk.eyJ1IjoiZHlsYW5iMTAxIiwiYSI6ImNsa3k1MnJpcDA3aTkzZHBodXdwaHdvNzkifQ.zj1-wMgJAfu_4-R6AGjhvw";

    lng = -71.224518;
    lat = 42.213995;
    zoom = 9;


    import { Map } from "mapbox-gl";
    

    import { onMount, onDestroy } from "svelte";

    onMount(() => {
        const initialState = { lng: lng, lat: lat, zoom: zoom};

        map = new Map({
            container: mapContainer,
            accessToken: MAPBOX_TOKEN,
            style: `mapbox://styles/mapbox/outdoors-v11`,
            center: [initialState.lng, initialState.lat],
            zoom: initialState.zoom
        })

    })





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

<body class="overflow-x-hidden">

    
    <div class="bg-blue-400 w-screen h-screen pt-4 pr-4">
        
        <div class="bg-white ml-4 mr-4 p-4 flex flex-row items-start gap-5 h-full">
            
            <!-- input container -->
            <div class="flex-grow w-full">
                
                <!-- search bar header -->
                <div class="text-lg mb-4 mt-4">
                    
                    <p class="">Starting Address</p>
                    
                </div>
                
                <!-- search bar -->
                <div class="flex gap-1">
                    
                    <input type="text" class="w-4/5 border-2 border-gray-400 rounded-md  hover:border-gray-500 transition ease-in-out bg-gray-100 text-black placeholder:text-gray-500 hover:drop-shadow-md flex-grow" placeholder="16 Roller Ave">

                    <button class="bg-zinc-500 border-2 rounded-md h-7 p-0.5 hover:drop-shadow-md transition ease-in-out ">
                        <img src="./my_location.svg" alt="My Location" class="h-full">
                    </button>
                    
                </div>
                
            </div>
            
            <!-- mapbox container -->
            
            <div class="flex-grow w-full h-4/5">
                
                <div class="w-full h-full" bind:this={mapContainer}></div>
                
            </div>


            
        </div>
        
    </div>
    
</body>