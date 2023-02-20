# Basic Vue form
Create basic form based on Vue for practice

Official documentation for Vue [click here](https://vuejs.org/guide/introduction.html)

<br>
<br>
Folow this instruction step by step, You can be easily create a basic form using Vue.js<br>
Lets' start<br>
<b>Step 1</b><hr><br>
copy a bootstrap boiler plate from bootstrap site with a basic form.<br>
or import all code from below
````
<!doctype html>
<html lang="en">

<head>
    <!-- Required meta tags -->
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1, shrink-to-fit=no">

    <!-- Bootstrap CSS -->
    <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap@4.0.0/dist/css/bootstrap.min.css" integrity="sha384-Gn5384xqQ1aoWXA+058RXPxPg6fy4IWvTNh0E263XmFcJlSAwiGgFAW/dAiS6JXm" crossorigin="anonymous">
</head>

<body>
    <div id="vue" class="container mt-4 vue">
        <h1>Hi, This is Zunaid Miah</h1>
        <hr><br>
        <p><b> This is a Vue Tutorial! Happy Coding</b></p>
        <hr><br>

        <form v-on:submit.prevent="doSomething">
            <div class="form-group">
                <label for="exampleInputEmail1">Email address</label>
                <input type="email" class="form-control" placeholder="Enter email">
                <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
            </div>
            <div class="form-group">
                <label for="exampleInputPassword1">First Name</label>
                <input type="text" class="form-control" placeholder="First name">
            </div>
            <div class="form-group">
                <label for="exampleInputPassword1">Last Name</label>
                <input type="text" class="form-control" placeholder="First name">
            </div>
            <div class="form-group">
                <label for="exampleInputPassword1">Your Age</label>
                <input type="text" class="form-control" placeholder="Your age">
            </div>
            <button type="submit" class="btn btn-primary mb-4">Submit</button>
            <br>
            <div v-if="status==1">
                <button class="btn btn-warning mb-4">Reset</button>
            </div>
        </form>
        <br>
    </div>

    <!-- Optional JavaScript -->
    <!-- jQuery first, then Popper.js, then Bootstrap JS -->
    <script src="https://code.jquery.com/jquery-3.2.1.slim.min.js" integrity="sha384-KJ3o2DKtIkvYIK3UENzmM7KCkRr/rE9/Qpg6aAZGJwFDMVNA/GpGFF93hXpG5KkN" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/popper.js@1.12.9/dist/umd/popper.min.js" integrity="sha384-ApNbgh9B+Y1QKtv3Rn7W3mgPxhU9K/ScQsAP7hUibX39j7fakFPskvXusvfa0b4Q" crossorigin="anonymous"></script>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@4.0.0/dist/js/bootstrap.min.js" integrity="sha384-JZR6Spejh4U02d8jOt6vLEHfe/JQGiRRSQQxSfFWpi1MquVdAyjUar5+76PVCmYl" crossorigin="anonymous"></script>
</body>

</html>
````

<br>
<br>
<b>Step 2</b><hr><br>
Now need to add vue cdn in head section <br>
```
<script src="https://unpkg.com/vue@3/dist/vue.global.js"></script>
```
<br>
<br>
<b>Step 3</b><hr><br>
Now add some vue code in script tag, given below
````
<script>
        const {
            createApp
        } = Vue

        createApp({
            data() {
                return {

                    name: "Zuanid Miah",
                    status: 0,
                    formData: {
                        email: 0,
                        fname: 0,
                        lname: 0,
                        age: 0,
                    },
                    matured: '<p style="color: blueviolet;">Hurray! You`re matured now! </p>',
                    adult: '<p style="color: green;">Hey! You`re adult now! </p>',
                    child: '<p style="color: red;">Oppps! You`re not adult! </p>'
                }
            },
            methods: {
                change() {
                    setTimeout(() => {
                        this.name = "Samima Akter Tithy"
                    }, 2000);
                },
                update() {
                    // setTimeout(() => {
                    this.name = "Zunaid Miah"
                        // },
                        // 2000);
                },
                alertMsg() {
                    alert("Hello i'm from event function!..");
                },
                doSomething() {
                    this.status = 1;
                },
                resetForm() {
                    this.status = 0;
                    this.formData.email = 0;
                    this.formData.fname = 0;
                    this.formData.lname = 0;
                    this.formData.age = 0;
                },
                dataHide() {
                    this.status = 0;
                }
            }
        }).mount("#vue")
    </script>
````
<br>
<br>
<b>Step 4</b><hr><br>
Add those div section under the form section
````
<div v-if="status==1">
    <p>Hey Welcome Mr.
        <strong> {{formData.fname }} {{formData.lname }}! </strong>, Your given information given below-</p>
    <p>Given Email is : {{ formData.email}}</p>
    <p>Given First Name is : {{ formData.fname}}</p>
    <p>Given Last Name is : {{ formData.lname}}</p>
    <p>Given Age is : {{ formData.age}}</p>
    <div v-if="formData.age>25" v-html="matured">
    </div>
    <div v-else-if="formData.age>=18" v-html="adult">
    </div>
    <div v-else v-html="child">
    </div>
</div>
````
 <br>
 <br>
 <b>Step 5</b><hr><br>
Now add directives and some of vue element on html DOM <br>
Replace the form section. <b> Know about directives [click here](https://vuejs.org/api/built-in-directives.html#built-in-directives) </b>
````
<form v-on:submit.prevent="doSomething">
    <div class="form-group">
        <label for="exampleInputEmail1">Email address</label>
        <input type="email" class="form-control" placeholder="Enter email" v-on:keydown="dataHide" v-model="formData.email">
        <small id="emailHelp" class="form-text text-muted">We'll never share your email with anyone else.</small>
    </div>
    <div class="form-group">
        <label for="exampleInputPassword1">First Name</label>
        <input type="text" class="form-control" placeholder="First name" v-on:keydown="dataHide" v-model="formData.fname">
    </div>
    <div class="form-group">
        <label for="exampleInputPassword1">Last Name</label>
        <input type="text" class="form-control" placeholder="Last name" v-on:keydown="dataHide" v-model="formData.lname">
    </div>
    <div class="form-group">
        <label for="exampleInputPassword1">Your Age</label>
        <input type="text" class="form-control" placeholder="Your age" v-on:keydown="dataHide" v-model="formData.age">
    </div>
    <button type="submit" class="btn btn-primary mb-4">Submit</button>
    <br>
    <div v-if="status==1">
        <button class="btn btn-warning mb-4" @click="resetForm">Reset</button>
    </div>
</form>
````
<br>
 <br>
 hurray!<br>
 So, you can test now by open your project in browser. <br>
 Or Browse this link<br>
 <h2>http://localhost:3000/ <?h2>
 <br><br>
 Thanks,<br>Zunaid Miah<br>
