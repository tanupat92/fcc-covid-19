<style>
    .columns {
        border: solid 1px black; 
    }
</style>

<script>
    export let usStats; 
</script>
<div class="section">
    <div class="container">
        <div class="columns">
            <h2 class="is-3 column">Cases:{usStats.cases}</h2>
            <h2 class="is-3 column">Deaths:{usStats.deaths}</h2>
            <h2 class="is-3 column">Recovered:{usStats.ventilator}</h2>
            <h2 class="is-3 column">Updated:{usStats.updated}</h2>
        </div>
    </div>
</div>
<div class="section">
    <div class="container">
        <div class="columns">
            <h2 class="is-3 column">Tested:{usStats.tested}</h2>
            <h2 class="is-3 column">Hospitalized:{usStats.hospitalized}</h2>
            <h2 class="is-3 column">Total ICU:{usStats.icu}</h2>
            <h2 class="is-3 column">Total Ventilator:{usStats.ventilator}</h2>
        </div>
    </div>
</div>