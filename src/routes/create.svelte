<script>
    let records;
    let first_name;
    let last_name;
    let title;
    let published;
    let text_type;
    let genre;
    async function submitData() {
        console.log("we're in the submission now");
        await fetch(`http://localhost:8080/create/text`, {
            method: "POST",
            headers: { "Content-Type": "application/json" },
            body: JSON.stringify([
                {
                    text_type,
                    // author_id: 0,
                    title,
                    published: parseInt(`${published}`),
                    metadata: { genre_tags: [`${genre}`] },
                },
                { first_name, last_name },
            ]),
        })
            .then((response) => response.json())
            .then((data) => (records = data))
            .catch((err) => console.log(err));
    }
</script>

<!-- CONTENT -->
<main>
    <div class="app">
        <form>
            <p>
                <label for="search">First Name: </label>
                <input
                    type="text"
                    id="first_name"
                    placeholder="William"
                    bind:value={first_name}
                />
            </p>
            <p>
                <label for="search">Last Name: </label>
                <input
                    type="text"
                    id="last_name"
                    placeholder="Shakespeare"
                    bind:value={last_name}
                />
            </p>
            <p>
                <label for="search">Published: </label>
                <input
                    type="text"
                    id="published"
                    placeholder="Year"
                    bind:value={published}
                />
            </p>
            <p>
                <label for="search">Title: </label>
                <input
                    type="text"
                    id="title"
                    placeholder="Hamlet"
                    bind:value={title}
                />
            </p>
            <p>
                <label for="search">Genre: </label>
                <input
                    type="text"
                    id="genres"
                    placeholder="Tragedy"
                    bind:value={genre}
                />
            </p>
            <p>
                <label for="text-types">Text Type:</label>
                <select name="text-types" id="text-types" bind:value={text_type}>
                    <option value="Novel">Novel</option>
                    <option value="Novella">Novella</option>
                    <option value="Play">Play</option>
                    <option value="Poem">Poem</option>
                </select>
            </p>
            <p>
                <button type="reset" on:click={submitData}>Submit</button>
            </p>
            {#if records}
                <p>SUCCESS!</p>
            {/if}
        </form>
    </div>
</main>

<!-- STYLING -->
<style>
    p {
        position: relative;
    }
    select {
        padding: 5px;
        padding-left: 18%;
        padding-right: 18%;
        font-size: 1.2em;
        position: relative;
        margin-top: 5px;
        margin-left: 160px;
        text-align: center;
    }
    label {
        position: absolute;
        text-align: center;
        width: 150px;
        left: 0;
        top: 20%; /* x to align nicely with the baseline of the text in the input */
    }
    input[type="text"] {
        padding: 5px 5px;
        font-size: 1.2em;
        margin: 8px;
        margin-left: 160px;
        box-sizing: border-box;
    }
    button[type="submit"] {
        align-self: center;
        margin-left: 80px;
        margin-top: 25px;
        /* margin-bottom: 50px; */
        padding: 5px;
        padding-left: 20%;
        padding-right: 20%;
        font-size: 1.2em;
        position: relative;
    }
</style>
