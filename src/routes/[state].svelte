<script context="module">
    import stateNames from '../data/stateNames.js'; 
    export async function preload(page) {
        const state = page.params["state"] 
        if (stateNames.find(s => s.abbreviation === state) === undefined){
            this.error(404, 'State Not Found'); 
            return ; 
        }
        try{
    
        } catch (e) {
            this.error(500, "Error in calling API");
            return ; 
        }
        return {state: page.params['state']};
    }
</script>

<script>
import CovidChart from "../components/CovidChart.svelte";
import CovidStat from "../components/CovidStat.svelte";

    export let state; 
</script>

<svelte:head>
    <title>Covid - {state}</title>
</svelte:head>

<div class="section header">
    <div class="container">
        <h1 class="title">Covid 19 {state}</h1>
    </div>
</div>


<CovidStat />
<CovidChart />