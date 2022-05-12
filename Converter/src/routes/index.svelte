<script>
    let inputValue = "0";
    let convertToFahrenheit = true;

    function switchState() {
        convertToFahrenheit = !convertToFahrenheit;
    }

    $: temperature = inputValue === null ? 0 : parseFloat(inputValue);
    $: fahrenheit = (Math.round((temperature * 1.8 + 32) * 100) / 100).toString() + ' °F';
    $: celsius = (Math.round((temperature - 32) * 5 / 9 * 100) / 100).toString() + ' °C';
</script>

<!-- (0 °C × 1.8) + 32 = 32 °F -->
<!-- (0 °F − 32) × 5/9 = -17,78 °C -->

<div class="w-screen h-screen flex flex-col items-center">
    <div class="text-[60px] mt-[9rem]">🌡️</div>
    <div class="text-xl w-[23rem] text-center m-3 mt-5">A simple web temperature converter built using Svelte.js and Tailwind CSS</div>
    <div class="text-2xl mt-[4rem] m-3 text-center font-bold">Mode: {convertToFahrenheit ? 'C' : 'F'}° → {convertToFahrenheit ? 'F' : 'C'}°</div>
    <input default="0" type="number" class="border-solid border-4 border-gradient p-2 font-bold text-xl text-center rounded-xl m-2 h-14 w-[220px] " bind:value={inputValue}>
    <button class="w-12 bg-gradient-to-tr bg-slate-800 p-3 m-2 h-12 rounded-3xl"><img src="https://i.ibb.co/NCMPx4v/swap.png" alt="go arrow" on:click={switchState}></button>
    <div class="text-2xl font-bold m-3">{inputValue === null ? "Input a number" : (convertToFahrenheit ? fahrenheit : celsius)}</div>
</div>