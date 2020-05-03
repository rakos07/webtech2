<template>
    <div>
        <h1>Login</h1>
        <div id="warningText" style="font-size: 20px; color: red">

        </div>
        <form v-on:submit.prevent="login">
            <div class="row">
                <div class="col-md-6">
                    <div class="form-group">
                        <label>Username</label>
                        <input id="name" type="text" class="form-control" v-model="item.name">
                    </div>
                </div>
            </div>
            <div class="row">
                <div class="col-md-6">
                    <div class="form-group">
                        <label>Password</label>
                        <input id="password" type="password" class="form-control col-md-6" v-model="item.price" />
                    </div>
                </div>
            </div><br />
            <div id="removable" class="form-group">
                <button class="btn btn-primary">Login</button>
            </div>
        </form>
    </div>
</template>
<script>
    var count = 3;
    export default {
        data(){
            return{
                item:{}
            }
        },
        methods: {
            login(){
                if(document.getElementById("name").value == "abc123" && document.getElementById("password").value == "abc123"){
                    this.$router.push({name: 'DisplayItem'})
                }
                else{
                    alert("Wrong username or password")
                    count--;
                    if(count > 0){
                        document.getElementById("warningText").innerText = "Remaing attempt: " + count
                    }
                    else{
                        if(count == 0){
                            document.getElementById("warningText").innerText = ""
                            document.getElementById("removable").innerHTML = "";
                        }
                    }
                }
            }
        }
    }
</script>

