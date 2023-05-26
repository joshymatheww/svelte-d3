<script>
    export let yScale;
    export let width;

    $: yTicks = yScale.ticks(4);
</script>

<g class="axis-y">
    {#each yTicks as tick, index}
        <g class="tick" transform="translate(0, {yScale(tick)})">
            <line
                x1="0"
                y1={0}
                x2={width}
                y2={0}
                stroke={index === 0 ? "#ddd" : "#333"}
            />
            <text x={"0"} y={0} fill="#f7f7f7" dy="-6">
                {tick}
                {index === yTicks.length - 1 ? " hours studied" : ""}
            </text>
        </g>
    {/each}
</g>
