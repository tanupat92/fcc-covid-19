<script>
    import { onMount, onDestroy } from "svelte";
    import Chart from 'chart.js/auto'; 
    import 'chartjs-adapter-moment'; // important for chart.js 3.9
    export let historicData;
    export let title;
  
    let hideChart = false;
    let chartElement;
    let chart;
  
    onMount(() => {
      if (historicData && document.body.clientWidth > 680) {
        createChart();
        return;
      }
  
      hideChart = true;
    });
  
    onDestroy(() => {
      if (chart) {
        chart.destroy();
      }
    });
  
    function createChart() {
      chart = new Chart(chartElement.getContext("2d"), {
        type: "line",
        data: {
          datasets: historicData
        },
        options: {
            responsive: true,
            plugins: {
                title: {
                    display: true,
                    text: title
                },
                tooltip: {
                    callbacks: {
                        label: function(tooltipItem, data) {
                            let label = data.datasets[tooltipItem.datasetIndex].label;
            
                            label += ": ";
            
                            label += tooltipItem.yLabel.toLocaleString();
            
                            return label;
                        }
                    }
                }
            },
            scales: {
                x: {
                    type: "time",
                    time: {
                        parser: "M/D/YY",
                        tooltipFormat: "ll"
                    },
                    title: {
                        display: true,
                        text: "Date"
                    }
                }
                ,
                y: {
                    title: {
                        display: true
                    },
                    beginAtZero: true,
                    ticks: {
                        callback: function(value, index, values) {
                            return value.toLocaleString();
                    }
                    }
                } 
            }
        }
      });
    }
  </script>
  
  {#if !hideChart}
    <div class="container">
      <canvas bind:this={chartElement} />
    </div>
  {/if}