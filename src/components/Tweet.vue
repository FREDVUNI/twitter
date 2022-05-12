<template>
    <div>
        <div class="card">
            <div class="card-body">
                <h4>@{{ username }}</h4>
                <p>{{ tweet.content }}</p>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'Tweet',
    props:["tweet","username"],
    data () {
        return {
            
        }
    }
}
</script>
<style>

</style>