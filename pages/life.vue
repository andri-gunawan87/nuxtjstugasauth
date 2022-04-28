<template>
    <div>
        <p id="life">{{message}}</p>
        
        <button class="btn btn-primary" @click="message = 'text berubah'">
            Update
        </button>
        </div>
</template>
<script>
export default {
    data() {
        return {
            message: "text awal",
        };
    },
    beforeCreate() {
        console.log("before created");
        // console.log(document.getElementById("life"));
    },
    created() {
        console.log("created");
        // console.log(document.getElementById("life"));
    },
    beforeMount() {
        console.log("beforeMount");
        // console.log(document.getElementById("life"));
    },
    mounted() {
        console.log("mounted");
        // console.log(document.getElementById("life"));
    },
    beforeUpdate() {
        console.log("beforeUpdate");
        console.log(document.getElementById("life").textContent);
    },
    updated() {
        console.log("Updated");
        console.log(document.getElementById("life").textContent);
    },
}
</script>