<script>
    import { fly } from 'svelte/transition';
    import {quadOut} from "svelte/easing";

    let projects = [
        { name: 'Pomodoro', url: 'https://pomodoro.manifesto-app.fr/', img: '/projects/pomodoro.png' },
        { name: 'Chrono', url: 'https://chrono.manifesto-app.fr/', img: '/projects/chrono.png' },
        { name: 'Keyboard trainer', url: 'https://trainerprogrammer.manifesto-app.fr/', img: '/projects/trainer.png' },
    ]
</script>

<section>
    {#each projects as project, i}
        <a href={project.url} class="card" in:fly|global={{
            delay: 100 * i + 300,
            duration: 300,
            easing: quadOut,
            y: 50,
            }}>
            <img src={project.img} alt={project.name} />
            <p>{project.name}</p>
        </a>
    {/each}
</section>

<style>
    section {
        columns: 310px;
        gap: 10px;
        max-width: 72rem;
        width: 100%;
        margin: 0 auto;
        box-sizing: border-box;
        padding: 0 1rem;
    }

    a {
        text-decoration: none;
        color: inherit;
    }

    .card {
        background-color: #ffffff00;
        backdrop-filter: blur(8px);
        border-radius: 10px;
        box-shadow: 0 2px 4px #00000030;
        transition: .3s;
        display: flex;
        flex-direction: column;
        break-inside: avoid;
        overflow: hidden;
        margin-bottom: 10px;
    }

    .card p {
        margin: 0;
        padding: 10px;
        font-weight: 700;
    }

    .card:hover {
        transform: translate(0, -4px);
    }

    .card:active {
        transform: translate(0, 0);
    }
</style>