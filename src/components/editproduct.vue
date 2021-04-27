<template>
    <form @click.prevent="handleUpdateForm">
        <center>
        <h1>แก้ไขสต็อกสินค้า</h1>
        </center>
        <div class="form-group">
            <label for="exampleInputEmail1">ชื่อสินค้า</label>
            <input type="Text" class="form-control" v-model="products.name">
        </div>
        <div class="form-group">
            <label for="exampleInputPassword1">คำอธิบายสินค้า</label>
            <input type="Text" class="form-control" v-model="products.detail">
        </div>
        <div class="form-group">
            <label for="exampleInputPassword1">ยี่ห้อ</label>
            <input type="Text" class="form-control" v-model="products.type">
        </div>
        <div class="form-group">
            <label for="exampleInputPassword1">ราคาสินค้า</label>
            <input type="Text" class="form-control" v-model="products.price">
        </div>
        <div class="form-group">
            <label for="exampleInputPassword1">สต็อก(จำนวน)</label>
            <input type="Text" class="form-control" v-model="products.stock">
        </div>
        <div class="form-group">
            <label for="exampleInputPassword1">ลิ้งรูปภาพ</label>
            <input type="Text" class="form-control" v-model="products.img">
            <center>
            <img :src="products.img" style="width: 20%;">
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
           products: {}
        }
    },
    created(){
        let apiURL = `http://mobliebackend.app.ruk-com.cloud/api/edit-product/${this.$route.params.id}`;
        axios.get(apiURL).then((res) => {
            this.product = res.data
        })
    },
    methods: { 
        handleUpdateForm(){
            let apiURL = `http://mobliebackend.app.ruk-com.cloud/api/update-product/${this.$route.params.id}`;

            axios.put(apiURL, this.products).then((res) => {
                console.log(res);

            }).catch(error => {
                console.log(error)
            })
        }
    }
}
</script>
