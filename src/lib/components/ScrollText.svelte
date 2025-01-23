<script lang="ts">
    import { onMount } from "svelte";
    import TextGradient from "./TextGradient.svelte";

    let position = 0;

    const onScroll = () => {
        position = window.scrollY / (document.body.scrollHeight - window.innerHeight) * 4;
    }
    onMount(() => {
        onScroll();
    });

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

    const sources = [
        "https://www.zdnet.com/article/switzerland-now-requires-all-government-software-to-be-open-source/",
        "https://ubuntu.com/blog/does-open-source-software-have-the-same-safety-as-proprietary-software",
        "https://www.commerce.gov/about/policies/source-code",
        "https://fedscoop.com/agencies-must-share-custom-source-code-under-new-share-it-act/"
    ]
</script>
<svelte:document on:scroll={onScroll} />

<div class="absolute w-full h-full text-white">
    <div class="relative h-screen flex flex-col justify-center items-center text-center">
        <div class="font-semibold flex flex-col items-center gap-4" style={fadeOut(position, 0.5, 0.75)}>
            <div class="text-4xl sm:text-6xl"><TextGradient className="font-extrabold" from="#ff0f7b" to="#f89b29">Imagine</TextGradient> a world</div>
            <div class="text-2xl">where all <i>government code</i></div>
            <div class="text-4xl sm:text-6xl">is <TextGradient className="font-extrabold" from="#84ffc9" via="#aab2ff" to="#eca0ff">Open Source</TextGradient>...</div>
        </div>
        <div class="absolute bottom-16 text-center" style={fadeOut(position, 0.0, 0.5)}>
            <div class="float text-gray-500">▼ Scroll Down ▼</div>
        </div>
    </div>


    <div class="relative h-screen flex flex-col justify-center items-end text-end">
        <div class="font-semibold flex flex-col items-center gap-4 pr-8" style={fadeInOut(position, 0.5, 1.0, 1.5)}>
            <div class="text-2xl sm:text-4xl">...where you can <TextGradient className="font-extrabold text-4xl sm:text-6xl" from="#e9b7ce" to="#d3f3f1">Trust</TextGradient></div>
            <div class="text-2xl sm:text-4xl">the voting machines...</div>
        </div>
    </div>

    <div class="relative h-screen"></div>
    <div class="fixed top-12 w-full flex flex-col items-center text-center" style={fadeInOut(position, 1.5, 2.0, 2.25)}>
        <div class="text-2xl sm:text-4xl">...and believe in the <TextGradient className="font-extrabold text-4xl sm:text-6xl" from="#ff1b6b" to="#45caff">Technology</TextGradient></div>
        <div class="text-2xl sm:text-4xl">that <TextGradient className="font-extrabold text-4xl sm:text-6xl" from="#fbd07c" to="#f7f779">Powers</TextGradient> our union...</div>
    </div>

    <div class="relative h-screen flex flex-col items-end text-end">
        <div class="font-semibold flex flex-col items-center gap-4 pt-24 pr-8" style={fadeInOut(position, 2.75, 3.0, 3.25)}>
            <div class="text-2xl sm:text-4xl">...because the <TextGradient className="font-extrabold text-4xl sm:text-6xl" from="#82f4b1" to="#30c67c">Code</TextGradient></div>
            <div class="text-2xl sm:text-4xl">is open to the <TextGradient className="font-extrabold text-4xl sm:text-6xl" from="#fffbaf" to="#ab2aed">People</TextGradient>...</div>
        </div>
    </div>

    <div class="fixed top-12 w-full flex flex-col items-center text-center" style={fadeInOut(position, 1.5, 2.0, 2.25)}>
        
    </div>
    <div class="relative min-h-screen flex flex-col items-center pt-12 pb-24 px-4" style={fadeIn(position, 3.25, 4.0)}>
        <div class="text-2xl sm:text-4xl font-semibold mb-12">
            to promote
        </div>
        <div class="w-full flex gap-8 flex-col items-center lg:flex-row lg:items-start lg:justify-evenly">
            <div class="flex flex-col items-center">
                <div class="text-2xl sm:text-2xl text-center"><TextGradient className="font-extrabold text-4xl sm:text-6xl" from="#caefd7" via="#f5bfd7" to="#abc9e9">Transparency</TextGradient>,</div>
                <div class="indent-4 text-balance pt-8 max-w-sm">
                    <p class="mb-4">
                        Requiring all government code to be open source will allow the public to see how the government works.
                        This will <b>increase trust in the government</b> and allow for more public oversight in the development of government software,
                        and will help to prevent corruption and abuse of power.
                    </p>
                    <p>
                        Right now, more than ever, it is important for the government to be transparent and accountable to the people. So we can remain a free and democratic society.
                    </p>
                </div>
            </div>
            <div class="flex flex-col items-center">
                <div class="text-2xl sm:text-4xl text-center"><TextGradient className="font-extrabold text-4xl sm:text-6xl" from="#0061ff" to="#60efff">Security</TextGradient>,</div>
                <div class="indent-4 text-balance pt-8 max-w-sm">
                    <p class="mb-4">
                        The biggest thing is that <b>obscurity is not security</b>. The more people that can see the code, the more people that can find and fix vulnerabilities.
                        This will make government software more secure and <b>less vulnerable to hacking</b> and other cyber attacks. Well maintained open source software is 
                        often more secure than closed source software because it is constantly being reviewed and improved by the community.
                    </p>
                    <p>
                        Exceptions exist for sensitive information such as military secrets, personal data, or copyrighted material.
                    </p>
                </div>
            </div>
            <div class="flex flex-col items-center">
                <div class="text-2xl sm:text-4xl text-center whitespace-nowrap">and <TextGradient className="font-extrabold text-4xl sm:text-6xl" from="#82f4b1" to="#30c67c">Innovation</TextGradient></div>
                <div class="indent-4 text-balance pt-8 max-w-sm">
                    <p>
                        This code was <b>paid for by our tax dollars</b>, and deserves to be available to the public to use and improve. Open source projects are often used as 
                        building blocks for other projects and valuable examples for developers. Having government code open source will allow for <b>more innovation</b> 
                        and help everyone to build better software.
                    </p>
                </div>
            </div>
        </div>
        <div class="w-3/4 my-16 h-[2px] bg-gray-600"></div>
        <div class="text-4xl sm:text-6xl">
            <TextGradient className="font-extrabold" from="#eca0ff" via="#aab2ff" to="#84ffc9">The Proposal</TextGradient>:
        </div>
        <div class="text-lg indent-4 text-balance mt-8 container text-center">
            <p class="mb-4 font-bold">
                We propose that 100% of custom developed software by government institutions, both federal and state, be open source, 
                unless exempt for the reason of security, personal data, or prevented by other laws.
            </p>
            <p class="mb-4">
                Additionally, this open source requirement extends to other contracted companies that develop software for vital government functions,
                such as voting machines, and other critical infrastructure that could benefit from transparency. The specifics of this policy still need to be worked out.
            </p>
            <p class="mb-4">
                This is an extension of the <a href="https://www.commerce.gov/about/policies/source-code" target="_blank" class="underline">U.S. Department of Commerce Source Code Policy</a>, which requires at least 20% of custom developed code to be open source.
                We believe it should be 100% and extend to the private sector on certain areas for the reasons stated above.
            </p>
        </div>
        <div class="w-3/4 my-16 h-[2px] bg-gray-600"></div>
        <div class="text-sm container text-center text-gray-500">
            <ul>
                {#each sources as source}
                    <li><a href={source} target="_blank" class="underline">{source}</a></li>
                {/each}
            </ul>
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