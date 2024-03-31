<script>
    let records;
    let author = "Shakespeare";
    async function getData() {
        const response = await fetch(`http://localhost:8080/texts/${author}`, {
            method: "GET",
        });
        if (response.status == 200) {
            console.log("Success");
            records = await response.json();
            console.log(records);
        } else {
            let status = records.status;
            records = 0;
            throw new Error(status);
        }
    }
</script>

<main>
    <div class="app">
        <label for="search">Last Name: </label>
        <input
            type="text"
            id="search"
            placeholder="Author Last Name"
            bind:value={author}
        />
        {#if records}
            <p>
                <strong>{records[0].first_name} {records[0].last_name}</strong>
            </p>
            {#each records as record}
                <li>
                    {record.title}: {record.published}
                </li>
            {/each}
        {:else if records == 0}
            <p>No Author matching that last name</p>
        {:else}
            <p>no data yet</p>
        {/if}
        <p>
            <button on:click={getData}>Get Data</button>
        </p>
    </div>
</main>

<style>
    li {
        list-style: decimal;
    }

    input[type="text"] {
        padding: 5px 5px;
        font-size: 1.2em;
        margin: 8px 0;
        box-sizing: border-box;
    }
</style>
