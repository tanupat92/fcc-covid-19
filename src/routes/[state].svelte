<script context="module">
    export async function preload(page) {
        return {state: page.params['state']}
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