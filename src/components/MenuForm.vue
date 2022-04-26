<template>
    <Form
        @submit="$emit('submit:menu', menuLocal)"
        :validation-schema="menuFormSchema"
    >
        <div class="form-group">
            <label for="name">Tên</label>
            <Field
                name="name"
                type="text"
                class="form-control"
                v-model="menuLocal.name"
            />
            <ErrorMessage name="name" class="error-feedback" />
        </div>
        <div class="form-group">
            <label for="price">Gía</label>
            <Field
                name="price"
                type="text"
                class="form-control"
                v-model="menuLocal.price"
            />
            <ErrorMessage name="price" class="error-feedback" />
        </div>
        <div class="form-group">
            <label for="processingtime">Thời gian chế biến</label>
            <Field
                name="processingtime"
                type="text"
                class="form-control"
                v-model="menuLocal.processingtime"
            />
            <ErrorMessage name="description" class="error-feedback" />
        </div>
        <div class="form-group">
            <label for="image">Link ảnh</label>
            <Field
                name="image"
                type="text"
                class="form-control"
                v-model="menuLocal.image"
            />
            <ErrorMessage name="image" class="error-feedback" />
        </div>

        <div class="form-group form-check">
            <input
                name="favorite"
                type="checkbox"
                class="form-check-input"
                v-model="menuLocal.trend"
            />
            <label for="favorite" class="form-check-label">
                <strong>Thích</strong>
            </label>
        </div>

        <div class="form-group">
            <button class="btn btn-primary">Lưu</button>
            <button
                v-if="menuLocal.id"
                type="button"
                class="ml-2 btn btn-danger"
                @click="$emit('delete:menu', menuLocal.id)"
            >
                Xóa
            </button>
        </div>
    </Form>
</template>

<script>
import * as yup from "yup";
import { Form, Field, ErrorMessage } from "vee-validate";

export default {
    components: {
        Form,
        Field,
        ErrorMessage,
    },
    emits: ["submit:menu", "delete:menu"],
    props: {
        menu: { type: Object, required: true }
    },
    data() {
        const menuFormSchema = yup.object().shape({
            name: yup
                .string()
                .required("Tên phải có giá trị.")
                .min(2, "Tên phải ít nhất 2 ký tự.")
                .max(100, "Tên có nhiều nhất 100 ký tự."),
            price: yup
                .string()
                .required("Giá tiền phải có giá trị.")
                .min(2, "Giá tiền phải ít nhất 2 ký tự.")
                .max(100, "Giá tiền có nhiều nhất 50 ký tự."),
            processingtime: yup
                .string()
                .required("Thời gian chế biến phải có giá trị.")
                .min(2, "Thời gian chế biến phải ít nhất 20 ký tự.")
                .max(100, "Thời gian chế biến có nhiều nhất 50 ký tự."),
            image: yup
                .string()
                .required("Ảnh phải có giá trị(đường link ảnh).")
        });
        return {
            menuLocal: this.menu,
            menuFormSchema,
        };
    },
};
</script>

<style scoped>
@import "@/assets/form.css";
</style>