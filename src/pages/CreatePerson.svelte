<script>
    import axios from "axios";

    let person = {
        birthdate: null,
        name: "",
    };

    function createPerson() {
        axios.post("http://localhost:8080/infections/persons", person)
            .then( response => {
                alert("Person was successfully created")
            })
    }
</script>

<h1>Create Person</h1>

<form>
    <div class="mb-3">
        <label class="form-label" for="">Name</label>
        <input class="form-control" type="text" bind:value={person.name} />
    </div>
    <div class="mb-3">
        <label class="form-label" for="">Birthdate</label>
        <input
            class="form-control"
            type="number"
            bind:value={person.birthdate}
        />
    </div>

    <button type="button" class="btn btn-primary" on:click={createPerson}>Create Person</button>
</form>
