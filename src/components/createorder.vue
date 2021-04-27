<template>
    <form @submit.prevent="handleSubmitForm">
        <center>
        <h1>เพิ่มสต็อกสินค้า</h1>
        </center>
        <div class="form-group">
            <label for="exampleInputEmail1">ชื่อสินค้า</label>
            <input type="Text" class="form-control" v-model="product.name" required>
        </div>
        <div class="form-group">
            <label for="exampleInputPassword1">คำอธิบายสินค้า</label>
            <input type="Text" class="form-control" v-model="product.detail" required>
        </div>
        <div class="form-group">
            <label for="exampleInputPassword1">ยี่ห้อ</label>
            <input type="Text" class="form-control" v-model="product.type" required>
        </div>
        <div class="form-group">
            <label for="exampleInputPassword1">ราคาสินค้า</label>
            <input type="Text" class="form-control" v-model="product.price" required>
        </div>
        <div class="form-group">
            <label for="exampleInputPassword1">สต็อก(จำนวน)</label>
            <input type="Text" class="form-control" v-model="product.stock" required>
        </div>
        <div class="form-group">
            <label for="exampleInputPassword1">ลิ้งรูปภาพ</label>
            <input type="Text" class="form-control" v-model="product.img" >
            <center>
            <img :src="product.img" style="width: 20%;">
            </center>
        </div>
        <center>
        <div class="clearfix">
        <router-link to="/stock"><button class="btn btn-danger" style="margin-right: 10%">Back</button></router-link>
        <button type="submit" class="btn btn-primary">Submit</button>
        </div>
        </center>
    </form>
</template>
<script>
import axios from 'axios';

export default {
    data(){
        return{
            product: {
               name: '',
               detail: '',
               type: '',
               price: '',
               stock: '',
               img: ''
            },
            selectedFile: null
        }
    },
    methods: {
        handleSubmitForm(){
            let apiURL = 'http://localhost:4000/api/create-product';

            axios.post(apiURL, this.product).then(() => {
                this.$router.push('/stock');
                this.product = {
                    name: '',
                    detail: '',
                    type: '',
                    price: '',
                    stock: '',
                    img: ''
                }
            }).catch(error => {
                console.log(error)
            })
        }
    }
}
</script>