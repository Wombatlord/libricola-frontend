<script>
    import Router from "svelte-spa-router";
    import Home from "./routes/home.svelte";
    import Create from "./routes/create.svelte";

    let routes = {
        "/": Home,
        "/create": Create,
    };
</script>

<main>
    <Router {routes} />
    <footer>
        <span>
            'Properly, we should read for power. Man reading should be man
            intensely alive. The book should be a ball of light in one's hand.'
            - Ezra Pound
        </span>
    </footer>
</main>

<style>
    footer {
        position: fixed;
        bottom: 0;
        left: 0;
        padding-top: 5px;
        padding-bottom: 5px;
        font-size: 1.2vw;
        width: 100vw;
        height: fit-content;
        background-color: #303c50;
    }

    span {
        color: #f4f1de;
    }
</style>
