<template>
    <table>
        <tr v-for="make in makes">
            <td >{{make.nome}}</td>
        </tr>
    </table>
</template>

<script>
export default {
    name: "makes-fav",
    props: ["makes"]

}
</script>

<style>

</style>