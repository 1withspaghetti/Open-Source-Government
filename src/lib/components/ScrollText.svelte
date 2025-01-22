<script lang="ts">
    import TextGradient from "./TextGradient.svelte";

    let position = 0;

    const onScroll = () => {
        position = window.scrollY / (document.body.scrollHeight - window.innerHeight) * 4;
    }

    // Helpers

    function map(value: number, start1: number, stop1: number, start2 = 0, stop2 = 1) {
        return start2 + (stop2 - start2) * ((value - start1) / (stop1 - start1));
    }

    function clamp(value: number, min: number, max: number) {
        return Math.min(Math.max(value, min), max);
    }

    function fadeIn(position: number, from: number, to: number) {
        return "opacity: "+clamp(map(position, from, to, 0, 1), 0, 1)+";";
    }

    function fadeOut(position: number, from: number, to: number) {
        return "opacity: "+clamp(map(position, from, to, 1, 0), 0, 1)+";";
    }

    function fadeInOut(position: number, from: number, at: number, to: number) {
        return "opacity: "+clamp(Math.min(map(position, from, at, 0, 1), map(position, at, to, 1, 0)), 0, 1)+";";
    }
</script>
<svelte:document on:scroll={onScroll} />

<div class="absolute w-full h-full text-white">
    <div class="relative h-screen flex flex-col justify-center items-center text-center">
        <div class="font-semibold flex flex-col items-center gap-4" style={fadeOut(position, 0.5, 0.75)}>
            <div class="text-6xl"><TextGradient className="font-extrabold" from="#ff0f7b" to="#f89b29">Imagine</TextGradient> a world</div>
            <div class="text-2xl">where all <i>government code</i></div>
            <div class="text-6xl">is <TextGradient className="font-extrabold" from="#84ffc9" via="#aab2ff" to="#eca0ff">Open Source</TextGradient></div>
        </div>
        <div class="absolute bottom-16 text-center" style={fadeOut(position, 0.0, 0.5)}>
            <div class="float text-gray-500">▼ Scroll Down ▼</div>
        </div>
    </div>


    <div class="relative h-screen flex flex-col justify-center items-end text-end">
        <div class="font-semibold flex flex-col items-center gap-4 pr-8" style={fadeOut(position, 1.0, 1.5)}>
            <div class="text-4xl">Where you can <TextGradient className="font-extrabold text-6xl" from="#e9b7ce" to="#d3f3f1">Trust</TextGradient></div>
            <div class="text-4xl">the voting machines...</div>
        </div>
    </div>

    <div class="relative h-screen"></div>
    <div class="fixed top-12 w-full flex flex-col items-center text-center" style={fadeInOut(position, 1.5, 2.0, 2.25)}>
        <div class="text-4xl">...and the <TextGradient className="font-extrabold text-6xl" from="#ff1b6b" to="#45caff">Technology</TextGradient></div>
        <div class="text-4xl">that <TextGradient className="font-extrabold text-6xl" from="#fbd07c" to="#f7f779">Powers</TextGradient> our union...</div>
    </div>

    <div class="relative h-screen flex flex-col items-end text-end">
        <div class="font-semibold flex flex-col items-center gap-4 pt-24 pr-8" style={fadeInOut(position, 2.75, 3.0, 3.25)}>
            <div class="text-4xl">...because the <TextGradient className="font-extrabold text-6xl" from="#82f4b1" to="#30c67c">Code</TextGradient></div>
            <div class="text-4xl">is open to the <TextGradient className="font-extrabold text-6xl" from="#fffbaf" to="#ab2aed">People</TextGradient>.</div>
        </div>
    </div>
</div>

<style>
    .float {
        animation: float 3s ease-in-out infinite;
    }

    @keyframes float {
        0% {
            transform: translatey(0px);
        }
        50% {
            transform: translatey(10px);
        }
        100% {
            transform: translatey(0px);
        }
    }
</style>