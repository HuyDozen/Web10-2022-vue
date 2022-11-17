<template>
    <div>
        Huy bếu
    </div>
</template>

<script>
export default {
    name: "DemoVue",// Tên của component (buộc phải có nhiều từ)
    props: ["FullName","Age"], // Thuộc tính của demo có nhận các giá trí bên ngoài
    methods: { // Phương thức của demo
        getName(){

        }
    },

    data() { // Dữ liệu của demo, bắt buộc phải là return, gtri trả về
        return {
            fullName:"",
            employees:[],
            emp:[]
        }
    },

}
</script>

<style scoped>

</style>
    
