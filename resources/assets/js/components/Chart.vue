<template>
	<div>
		<canvas :id="id" width="width" height="height"></canvas>
	</div>
</template>

<script>
   	export default {
		props: [
			'type', 
			'id',
			'width',
			'height',
			'dimension',
			'label',
			'background',
			'border',
			'label',
			'data',
			'labels',
		],
		data: function() {
		    return {
		    	typeChart:      this.type,
		    	idChart:        this.id,
		    	labelsChart:    this.labels,
		    	labelMain:      this.label,
		    	dataChart:      this.data,
		    	dimensionChart: this.dimension,
		    	chartBackground:this.background,
		    	chartBorder:    this.border,
			}
		},
	    methods: {
	        generateChart() {
			    let ctx = document.getElementById(this.idChart).getContext(this.dimensionChart);
			    let myChart = new Chart(ctx, {
			        type: this.typeChart,
			        data: {
			            labels: JSON.parse(this.labelsChart),
			            datasets: [{
			                label: this.labelMain,
			                data: JSON.parse(this.data),
			                backgroundColor: JSON.parse(this.chartBackground),
			                borderColor: JSON.parse(this.chartBorder),
			                borderWidth: 1
			            }]
			        },
			        options: {
			            scales: {
			                yAxes: [{
			                    ticks: {
			                        beginAtZero: true
			                    }
			                }]
			            }
			        }
			    });
	        }
	    },
	    mounted: function() {
		    this.generateChart();
		},
   }
</script>