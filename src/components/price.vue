<template>
    <span>{{ this.value | formatCurrency}}</span>
</template>

<script>
export default{
    name: 'price',
    filters : {
        formatCurrency(number) {
        const locale = "id-ID";
        const options = { style: "currency", currency: "IDR" };
        const formatter = new Intl.NumberFormat(locale, options);
        return formatter.format(number);
      }
    },
    props:{
        value : Number
    }
}
</script>