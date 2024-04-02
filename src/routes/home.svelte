<script>
    let records;
    let author = "Shakespeare";
    async function getData() {
        await fetch(`http://localhost:8080/texts/${author}`, {
            method: "GET",
        })
            .then((response) => response.json())
            .then((data) => (records = data))
            .catch((err) => console.log(err));
    }
</script>


<main>
    <div class="search-wrapper">
        <input
            type="text"
            id="search"
            placeholder="Author Last Name"
            bind:value={author}
        />
        <button on:click={getData}
            ><span class="material-symbols-outlined"> search </span></button
        >
    </div>
    <div class="records">
        {#if records == "No title & author pairings found."}
            <p>No Author matching that last name</p>
        {:else if records}
            {#each Object.keys(records) as author}
                <div class="texts">
                    <p>
                        <strong><span class="author"><em>{author}</em></span></strong>
                    </p>
                    <div class="entries">
                        {#each Object.entries(records[author]) as title}
                            <li>
                                <span class="titles"
                                    >{title[0]} : {title[1]}</span
                                >
                            </li>
                        {/each}
                    </div>
                </div>
            {/each}
        {:else}
            <h2><em><strong>Libricola, Libricolae</strong></em></h2>
            <p>/lˌiːbɹɪkˈo͡ʊlə/</p>
            <p>Noun</p>
            <p>Declension: 1st declension</p>
            <p>Gender: masculine</p>
            <h3>Definitions</h3>
            <p>1. Bibliophile, a lover of books.</p>
        {/if}
        <p></p>
    </div>
</main>

<style>
    .material-symbols-outlined {
        font-size: 1em;
        font-variation-settings:
            "FILL" 0,
            "wght" 400,
            "GRAD" 0,
            "opsz" 24;
    }
    main {
        display: flex;
        flex-direction: column;
        align-items: center;
    }

    h2 {
        font-family: Inter;
        font-size: 4em;
        margin: 0em 0 25px;
    }

    li {
        list-style: decimal;
        /* list-style-position: inside; */
        text-align: center;
        /* padding-left: 8rem; */
    }

    li::marker {
        color: #3b4473;
        font-size: 1.2em;
    }

    input[type="text"] {
        padding: 5px 5px;
        font-size: 1.2em;
        margin: 8px 0;
        box-sizing: border-box;
    }

    span.author {
        font-size: 5em;
        color: #f4f1de;
        font-family: Inter;
    }

    span.titles {
        font-size: 1.2em;
        color: #f4f1de;
        font-family: Inter;
    }

    .texts {
        padding-bottom: 25px;
        margin-bottom: 5vh;
        border-top: 4px solid;
        border-bottom: 4px solid;
        border-width: 3px;
        border-color: #3b4473;
        max-width: 100%;
    }
    .entries {
        align-content: center;
    }

    .search-wrapper {
        position: relative;
        max-width: max-content;
        display: flex;
        align-items: center;
        margin-bottom: 3.7em;
    }

    .search-wrapper input {
        width: 35ch;
        min-width: 1ch;
        border: 1px solid;
        border-radius: 6px 0px 0px 6px;
        color: #f4f1de;
        text-align: center;
    }

    input:focus {
        border-color: #008bce;
        outline-style: none;
    }

    .search-wrapper button {
        padding-top: 6px;
        padding-bottom: 6px;
        border: 1px solid;
        background-color: #303c50;
        color: #f4f1de;
        cursor: pointer;
        border-radius: 0px 6px 6px 0px;
    }

    button:hover {
        border-color: #008bce;
        box-shadow: none;
    }

    .records {
        margin-bottom: 5em;
    }
</style>
