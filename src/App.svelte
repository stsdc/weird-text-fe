<script>
    import "carbon-components-svelte/css/white.css";
    import {
        Header,
        Button,
        SkipToContent,
        TextArea,
    } from "carbon-components-svelte";

    let isSideNavOpen = false;
    let text = "Lorem Ipsum is simply dummy text of the printing and typesetting industry.";
    let encoded_text = "";
    let decoded_text = "";


    async function doPostEncode() {
        const res = await fetch("https://kkjijk.herokuapp.com/v1/encode", {
            method: "POST",
            headers: {
            'Content-Type': 'application/json'
            },
            body: JSON.stringify({
                "text": text,
            }),
        });

        const json = await res.json();
        encoded_text = JSON.parse(JSON.stringify(json))["encoded_text"];
        console.log(encoded_text);
    }

    async function doPostDecode() {
        const res = await fetch("https://kkjijk.herokuapp.com/v1/decode", {
            method: "POST",
            headers: {
            'Content-Type': 'application/json'
            },
            body: JSON.stringify({
                "encoded_text": encoded_text,
            }),
        });

        const json = await res.json();
        decoded_text = JSON.parse(JSON.stringify(json))["decoded_text"];
        console.log(decoded_text);
    }
</script>

<svelte:head>
    <title>Weird Text</title>
    <link
        rel="icon"
        href="data:image/svg+xml,<svg xmlns=%22http://www.w3.org/2000/svg%22 viewBox=%220 0 100 100%22><text y=%22.9em%22 font-size=%2290%22>✨</text></svg>"
    />
</svelte:head>

<Header company="" platformName="✨ Weird Text" bind:isSideNavOpen>
    <div slot="skip-to-content">
        <SkipToContent />
    </div>
</Header>

<main>
    <TextArea labelText="Encode some text:" placeholder="Enter your text..." bind:value={text}/>
    <Button on:click={doPostEncode}>Encode</Button>
    <span>{encoded_text}</span>

    <Button on:click={doPostDecode}>Decode</Button>
    <span>{decoded_text}</span>

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
