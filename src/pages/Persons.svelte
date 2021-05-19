<script>
    import axios from "axios";
    import { onMount } from "svelte";

    let persons = [];

    onMount(() => {
        getPersons();
    });

    function getPersons() {
        axios
            .get("http://localhost:8080/infections/persons")
            .then((response) => {
                persons = response.data;
            });
    }
</script>

<h1>This is a list of persons</h1>

<a href="#/create-person">+ Add Person</a>

<table class="table">
    <thead>
        <tr>
            <th>ID</th>
            <th>Name</th>
            <th>Birthdate</th>
        </tr>
    </thead>
    <tbody>
        {#each persons as person}
            <tr>
                <td><a href={"#/persons/"+person.id}>{person.id}</a></td>
                <td>{person.name}</td>
                <td>{person.birthdate}</td>
            </tr>
        {/each}
    </tbody>
</table>
