<script>
    import { fly } from 'svelte/transition'
    export let src, alt
    export let delay = 250;
</script>

<div>
    <img {src} {alt}>
    <h1 in:fly={{ x: -50, delay}}><slot name="role" /></h1>
    <p  in:fly={{ y: 50, delay}}><slot name="name"/></p>
</div>

<style>
    div {
        display: grid;
        grid-template-columns: 90% 1fr;
        grid-template-rows: 1fr min-content;

        width: clamp(156px, 100%, 264px);
        height: clamp(237px, 100%, 383px);
        transition: transform 250ms ease-in-out;
    }

    div:hover {
        transform: scale(1.2);
    }

    img {
        width: 100%;
        height: 100%;
    }

    h1 {
        color: black;
        font-size: 12px;
        line-height: 16px;
        font-weight: 400;
        font-style: normal;
        justify-self: end;
        writing-mode: vertical-lr;
        text-transform: uppercase;
    }

    p {
        font-size: 18px;
        font-weight: 600;
        line-height: 27px;
        margin-top: 15px;
    }

    @media (max-width: 1303px) {
        div:hover {
            transform: scale(1.1);
        }
    }
</style>