<script>
    import { Modals, closeModal, openModal } from "svelte-modals"
    import Modal from "./Modal.svelte"

    async function updateScissor(data) {
        const json = {
            redirect: data.redirect,
            scissor: data.scissor,
            random: data.random
        }
        await fetch("http://localhost:3000/scissor", {
            method: "POST",
            headers: {"Content-Type": "application/json"},
            body: JSON.stringify(json)
        }).then(response => {
            console.log(response)
        })
    }

    function handleOpen() {
        openModal(Modal, {
            title: "Create New Scissor Link",
            send: updateScissor,
            redirect: "",
            scissor: "",
            random: false
        })
    }
</script> 

<button on:click={ handleOpen }>New</button>

<style>
    button {
        background-color: green;
        color: white;
        font-weight: bold;
        border: none;
        padding: .75rem;
        border-radius: 4px;
    }
</style>