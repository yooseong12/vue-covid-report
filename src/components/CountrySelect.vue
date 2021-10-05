<template>
<!-- v-model = 폼 입력 태그 input 태그와 textarea태그 등에서 사용가능 -->
    <select @change="onchange()"
    v-model="selected" class="form-select mt-10 block w-full border p-3 
    rounded">
        <option value="0">Select Country</option>
        <option v-for="country in countries" :value="country.ID" :key="country">
            {{country.Country}}
        </option>
    </select>
</template>

<script>
export default {
    name: 'CountrySelect',
    props :['countries'],
    data(){
        return{
            selected:0,
        }
    },
    methods: {
        onchange(){
            const country = this.countries.find((item) => item.ID === this.selected)


            // $emit 하위 컴포넌트에서 상위 컴포넌트로 통신하는 방식
            this.$emit('get-country', country)
        }
    }
}
</script>