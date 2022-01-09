<script>
    import "carbon-components-svelte/css/white.css";
    import {
        Header,

        Button,
        SkipToContent,
        TextArea
    } from "carbon-components-svelte";

    let isSideNavOpen = false;

</script>

<svelte:head>
    <title>Weird Text</title>
    <link rel="icon" href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 100 100%22><text y=%22.9em%22 font-size=%2290%22>✨</text></svg>">
</svelte:head>

<Header company="" platformName="✨ Weird Text" bind:isSideNavOpen>
    <div slot="skip-to-content">
        <SkipToContent />
    </div>
</Header>

<main>
    <TextArea labelText="App description" placeholder="Enter your text..." />
    <Button>Encode</Button>
    <span>ddd</span>

</main>

<style>

    main {
        margin-top: 3.5rem;
        margin-left: 1rem;
        margin-right: 1rem;
        display: flex;
        flex-direction: column;
        flex-wrap: wrap;
        justify-content: space-evenly;
    }
    main :global(.el) {
        width: 50rem;
    }

    @media (min-width: 640px) {
        main {
            max-width: none;
        }
    }
</style>
