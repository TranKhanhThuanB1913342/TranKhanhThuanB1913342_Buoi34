<template>

    <h4>Thêm Liên hệ</h4>
    <!-- <AddNewForm @submit:contact="addContact" /> -->
    <AddNewForm />
    <p>{{ message }}</p>
    <!-- <div v-if="contact" class="page">
        <h4>Thêm Liên hệ</h4>
        <AddNewForm :contact="contact" @submit:contact="addContact" @delete:contact="deleteContact" />
        <p>{{ message }}</p>
    </div> -->
</template>
<script>
import AddNewForm from "@/components/AddNewForm.vue";
import ContactService from "@/services/contact.service";
export default {
    components: {
        AddNewForm: AddNewForm,
    },
    data() {
        return {
            contact: null,
            message: "",
        };
    },
    methods: {
        async addContact(data) {
            try {
                await ContactService.create(data);
                this.message = "Liên hệ được thêm thành công.";
            } catch (error) {
                console.log(error);
            }
        },
    },
    created() {
        this.message = "";
    },
};
</script>