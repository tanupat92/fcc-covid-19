<script context="module">
    import requests from "../data/requests.js"; 
    export async function preload() {
        try {
            //throw new Error('this is bad :(');
            const usStats = await requests.usStats();
            return {usStats}; 
        }
        catch (e) {
            this.error(500, "Error in calling API");
            return  
        }
    }
</script>
<script>
    import CovidStat from "../components/CovidStat.svelte";
    import CovidChart from "../components/CovidChart.svelte";
    import TableContainer from "../components/TableContainer.svelte";
import Error from "./_error.svelte";

    export let usStats;
    console.log(usStats, "usStats"); 
</script>

<svelte:head>
    <title>Covid Tracker</title>
</svelte:head>

<div class="section header">
    <div class="container">
        <h1 class="title">Covid 19 US</h1>
    </div>
</div>
<CovidStat {usStats}/>
<CovidChart />
<TableContainer />