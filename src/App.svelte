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

<div>
    <h1>My Super Sick Frontend.</h1>
    Last Name: <input bind:value={author} placeholder="Author Last Name" />
    {#if records}
        <p>
            <strong>{records[0].first_name} {records[0].last_name}</strong>
        </p>
        {#each records as record}
            <p>
                {record.title}: {record.published}
            </p>
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
