<template>
    <div >
        <table>
            <thead>
                <th>Id</th>
                <th>Title</th>
                <th>userId</th>
                <th>Body</th>
            </thead>
            <tbody>
                <tr v-for="data in data" :key="data.body">
                    <td>{{ data.id }}</td>
                    <td>{{ data.title }}</td>
                    <td>{{ data.userId }}</td>
                    <td>{{data.body}}</td>
                </tr>
            </tbody>
        </table>
    
    </div>
</template>

<script>
    export default {
        name:"PostsComponents",
        props:['data']

    }
</script>

<style scoped>
table{
    width: 100%;
    border-collapse: collapse;

}
th,td{
    padding: 4px;
    border: black 1px solid;
    text-align: center;
}
th{
    background-color: aliceblue;
}

</style>