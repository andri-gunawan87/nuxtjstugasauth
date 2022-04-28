<template>
<h1>Client Storage</h1>
</template>

<script>

const user = { first: 'Victoria', last: 'AAA' }

localStorage.setItem('user', JSON.stringify(user));

console.log(JSON.parse(localStorage.getItem('user')))

const update = { first: 'Victoria', last: 'Lo' }

localStorage.setItem('user', JSON.stringify(update));

</script>