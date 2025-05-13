<svelte:head>
    <title>Manifesto</title>
    <meta name="description" content="A boilerplate for Manifesto apps" />

    <!-- SEO -->
    <meta name="keywords" content="productivity, Manifesto, manifesto app" />
    <meta name="robots" content="index, follow" />
    <!-- Open Graph tags for social media platforms -->
    <meta property="og:title" content="Manifesto" />
    <meta property="og:description" content="The best productivity apps" />
    <meta property="og:image" content="URL to your preview image" />
    <meta property="og:url" content="URL of your site or page" />
    <meta property="og:type" content="website" />
</svelte:head>

<script>
    import List from "./List.svelte";
    import { fly, slide } from 'svelte/transition';
    import {quadInOut} from "svelte/easing";
    import {onMount} from 'svelte';

    const bars = ['/M1.png', '/M23.png', '/M23.png'];

    let showM  = false;
    let showText = false;

    onMount(() => {
        showM = true;
        setTimeout(() => showText = true, 2000);
    });
</script>


<h1>Manifesto</h1>

<div class="container">
    {#if showM}
        <div class="M" >
            {#each bars as bar, i}
                <img class="M-bars" src={bar} alt="M"
                     transition:fly|global={{ y: 100, delay: 200 * i , duration: 1000, easing: quadInOut }}
                >
            {/each}
        </div>
    {/if}

    {#if showText}
        <p in:slide={{ duration: 1000, easing: quadInOut, axis : 'x'}}>anifesto</p>
    {/if}
</div>

{#if showText}
    <List />
{/if}

<style>
    h1 {
        position: absolute;
        opacity: 0;
    }

    .container {
        display: flex;
        height: 80vh;
        margin: 0 auto;
        align-items: center;
    }

    .M-bars {
        height: 28vh;
    }

    .M {
        margin-bottom: 3vh;
    }

    p {
        font-size: 10vw;
        color: var(--color-theme-1);
        margin: 0;
    }

    @media ( max-width : 700px) {
        p {
            display: none;
        }

    }

</style>