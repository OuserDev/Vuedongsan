<template>
    <div class="discount">
        <h4>지금 결제하면 {{ dcper }}% 할인</h4>
    </div>
</template>

<script>
export default { 
    name:'Discount',
    data() {
        return {
            dcper: 30,
        }
    },
    mounted() {
        this.minus_per();
    },
    methods: {
        minus_per() {
            if (this.dcper > 0) {
                setTimeout(() => {
                this.dcper -= 1;
                this.minus_per();
                }, 1000);
            }
        }
    },
}
</script>

<style>
    .discount {
    background: #eee;
    padding:10px;
    margin:10px;
    }
</style>