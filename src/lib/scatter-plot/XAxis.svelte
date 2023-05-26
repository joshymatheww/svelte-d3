<script>
    let ticks = [0, 25, 50, 75, 100];

    export let height;
    export let xScale;
    export let width;
</script>

<g class="axis-x" transform="translate(0, {height})">
    {#each ticks as tick, index}
        <g class="tick" transform="translate({xScale(tick)}, 0)">
            <line x1={0} x2={0} y1={0} y2={6} stroke="#ddd" />
            <text
                fill="#ddd"
                x={0}
                y={6}
                dy={10}
                dominant-baseline="middle"
                text-anchor={index === 0 ? "start" : "middle"}
            >
                {tick}%
            </text>
        </g>
    {/each}
    <text
        x={width}
        y={0}
        dominant-baseline="start"
        text-anchor="end"
        dy={-10}
        fill="#ddd"
        class="axis-title"
    >
        Final Grade &rarr;
    </text>
</g>
