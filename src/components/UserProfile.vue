<template>
    <div>
        <div class="container">
            <div class="col-md-12">
                <div class="row">
                    <div class="col-md-4">
                        <div class="card">
                            <div class="card-body">
                                <h4>{{ this.fullname }}</h4>
                                <h6>@{{ this.user.username }}</h6>
                                <p>Follwers: {{ this.followers }}</p>
                                <button class="btn btn-sm btn-primary mr-3" v-if="this.user.isAdmin">Admin</button>
                                <br><br>
                                <form @submit.prevent="tweet()" class="formDisplay" :class="{'exceed':this.tweetlength > 180 }">
                                    <div class="form-group">
                                    <label for="tweet">New Tweet <b>{{ this.tweetlength }}/180</b></label>
                                    <textarea  id="" rows="5" class="form-control" v-model="atweet"></textarea>
                                </div>
                                <div class="form-group">
                                    <label for="Tweetype">Tweet Type</label>
                                    <select class="form-control" v-model="selectedtype">
                                        <option :value="tweetype.value" v-for="(tw,index) in tweetype" :key="index">{{ tw.name }}</option>
                                    </select>
                                </div>
                                <div class="form-group">
                                    <button type="submit" class="btn btn-dark btn-sm">Tweet</button>
                                </div>
                                </form>
                            </div>
                        </div>
                    </div>
                  <div class="col-md-8">
                       <Tweet v-for="tweet in user.tweets" :key="tweet.id" :tweet="tweet" :username="user.username"/>
                  </div>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import Tweet from './Tweet';
export default {
    name: 'UserProfile',
    data(){
        return{
        followers:0,
        selectedtype:"Instant",
        atweet:"",
        tweetype:[
            {"value":"draft","name":"Draft tweet"},
            {"value":"instant","name":"Instant tweet"},
        ],
        user:{
            id:1,
            username: 'fredvuni',
            firstname: 'Fred',
            lastname:'vuni',
            isAdmin:true,
            tweets:[
                {id:1,content:'Taking out a bunch of stuff'},
                {id:2,content:'Welcome to the twotter world'}
            ],
        },
        }
    },
    components:{
        Tweet
    },
    methods:{
        tweet(){
            if(this.atweet && this.selectedtype !== 'draft'){
                this.user.tweets.unshift({
                    id:this.user.tweets.length + 1,
                    content:this.atweet
                })
                this.atweet = "";
            }
        }
    },
    computed:{
        fullname(){
        return `${this.user.firstname} ${this.user.lastname}`
        },
        tweetlength(){
            return this.atweet.length
        }
    },
    mounted(){
        this.tweet()
        return this.followers
        }
    }
</script>
<style scoped>
    .exceed textarea{
        color: red;
        border-color: red;
    }
    .exceed label{
        color: red;
    }
    .exceed select{
        color: red;
        border-color: red;
    }
</style>