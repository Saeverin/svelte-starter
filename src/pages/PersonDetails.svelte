<script>
import axios from "axios";


    export let params = {};

    let personId;
    let person = {};
    
    $: {
        personId = params.id;
        getPerson();
    }

    function getPerson() {
        axios.get("http://localhost:8080/infections/persons/"+personId)
            .then( response => {
                person = response.data;
            })
    }
    
</script>

<h1>Person Details ({personId})</h1>

<p>Name: {person.name}</p>
<p>Birthdate: {person.birthdate}</p>