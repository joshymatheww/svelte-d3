<script>
    import { max, scaleLinear } from "d3";
    import data from "../../data/data";
    import XAxis from "./XAxis.svelte";
    import YAxis from "./YAxis.svelte";

    let width = 400;
    let height = 400;

    const margin = { top: 20, right: 15, bottom: 20, left: 0 };

    $: innerWidth = width - margin.left - margin.right;
    let innerHeight = height - margin.top - margin.bottom;

    $: xScale = scaleLinear().domain([0, 100]).range([0, innerWidth]);

    let yScale = scaleLinear()
        .domain([0, max(data, (d) => d.hours)])
        .range([innerHeight, 0]);
</script>

<div class="chart-container" bind:clientWidth={width}>
    <h2>Scatterplot:</h2>
    <svg {width} {height}>
        <g transform="translate({margin.left} {margin.top})">
            <XAxis height={innerHeight} {xScale} width={innerWidth} />
            <YAxis {yScale} width={innerWidth} />
            {#each data as d}
                <circle
                    cx={xScale(d.grade)}
                    cy={yScale(d.hours)}
                    r="10"
                    fill="purple"
                    stroke="black"
                    stroke-width="1"
                />
            {/each}
        </g>
    </svg>
</div>

<style>
    .chart-container {
        border: 1px solid #ddd;
        padding: 20px;
    }
</style>
