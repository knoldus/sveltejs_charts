<script>
	import Chart from "chart.js/auto";
	import { onMount } from "svelte";
	const data = {
		labels: [
			"January",
			"February",
			"March",
			"April",
			"May",
			"June",
			"July",
		],
		datasets: [
			{
				label: "Dataset",
				backgroundColor: "rgba(255,99,132,0.2)",
				borderColor: "rgba(255,99,132,1)",
				borderWidth: 1,
				hoverBackgroundColor: "rgba(255,99,132,0.4)",
				hoverBorderColor: "rgba(255,99,132,1)",
				data: [65, 59, 80, 81, 56, 55, 40],
			},
		],
	};

	let pieChart, barChart, lineChart;

	const options = {
		scales: {
			yAxes: [{ ticks: { beginAtZero: true } }],
		},
	};

	onMount(() => {
		const pieCtx = pieChart.getContext("2d");
		const pieChartObj = new Chart(pieCtx, {
			type: "pie",
			data: data,
			options: options,
		});

		const barCtx = barChart.getContext("2d");
		const barChartObj = new Chart(barCtx, {
			type: "bar",
			data: data,
			options: options,
		});

		const lineCtx = lineChart.getContext("2d");
		const lineChartObj = new Chart(lineCtx, {
			type: "line",
			data: data,
			options: options,
		});
	});
</script>

<h1>Charts example in svelteJs</h1>


<canvas bind:this={pieChart} />
<canvas bind:this={barChart} />
<canvas bind:this={lineChart} />

<style>
	h1{
		text-align: center;
	}
	canvas {
		text-align: center;
		padding: 1em;
		width: 500px;
		height: 500px;
		margin: 4rem auto;
	}
</style>
