<script>
    import Router from "svelte-spa-router";
    import Home from "./routes/home.svelte";
    import Create from "./routes/create.svelte";
    import About from "./routes/about.svelte";

    let routes = {
        "/": Home,
        "/about": About,
        "/create": Create,
    };
</script>

<main>
    <Router {routes} />
</main>
