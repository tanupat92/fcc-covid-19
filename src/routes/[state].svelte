<script context="module">
    import stateNames from '../data/stateNames.js'; 
    import requests from '../data/requests.js'; 
    export async function preload(page) {
        const state = page.params["state"] 
        if (stateNames.find(s => s.abbreviation === state) === undefined){
            this.error(404, 'State Not Found'); 
            return ; 
        }
        try{
            const stats = await requests.stateStats(state); 
            return {state, stats};
        } catch (e) {
            this.error(500, "Error in calling API");
            return ; 
        }
        
    }
</script>

<script>
import CovidChart from "../components/CovidChart.svelte";
import CovidStat from "../components/CovidStat.svelte";

export let state;
export let stats;  
</script>

<svelte:head>
    <title>Covid - {state}</title>
</svelte:head>

<div class="section header">
    <div class="container">
        <h1 class="title">Covid 19 {state}</h1>
    </div>
</div>


<CovidStat usStats={stats} />
<CovidChart />