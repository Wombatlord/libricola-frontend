<script>
    async function submitData() {}
</script>

<main>
    <div class="app">
        <form action="post">
            <p>
                <label for="search">First Name: </label>
                <input type="text" id="search" placeholder="William" />
            </p>
            <p>
                <label for="search">Last Name: </label>
                <input type="text" id="search" placeholder="Shakespeare" />
            </p>
            <p>
                <label for="search">Published: </label>
                <input type="text" id="search" placeholder="Year" />
            </p>
            <p>
                <label for="search">Title: </label>
                <input type="text" id="search" placeholder="Hamlet" />
            </p>
            <p>
                <label for="search">Genre: </label>
                <input type="text" id="search" placeholder="Tragedy" />
            </p>
            <p>
                <label for="text-types">Text Type:</label>
                <select name="text-types" id="text-types">
                    <option value="Novel">Novel</option>
                    <option value="Novella">Novella</option>
                    <option value="Play">Play</option>
                    <option value="Poem">Poem</option>
                </select>
            </p>
            <p>
                <input type="submit" value="Submit" on:click={submitData} />
            </p>
        </form>
    </div>
</main>

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
    input[type="submit"] {
        align-self: center;
        margin-left: 80px;
        margin-top: 25px;
        margin-bottom: 50px;
        padding: 5px;
        padding-left: 20%;
        padding-right: 20%;
        font-size: 1.2em;
        position: relative;
    }
</style>
