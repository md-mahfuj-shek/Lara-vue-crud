<script setup lang="ts">
import AppLayout from '@/layouts/AppLayout.vue';
import { type BreadcrumbItem } from '@/types';
import { Head, Link } from '@inertiajs/vue3';
import { Input } from '@/components/ui/input';
import { Label } from '@/components/ui/label';
import { Button } from '@/components/ui/button';
import { useForm } from '@inertiajs/vue3'

const breadcrumbs: BreadcrumbItem[] = [
    {
        title: 'Create a Product',
        href: '/products/create'
    }
];

const form = useForm({
    name: '',
    price: '',
    description: '',
})

const handleSubmit = () => {
    form.post(route('products.store'));
}
</script>

<template>
    <Head title="Create a Product" />

    <AppLayout :breadcrumbs="breadcrumbs">
        <div class="p-4">
            <form @submit.prevent="handleSubmit" class="w-6/12 space-y-4">
                <div class="space-y-2">
                    <Label for="Product name">Name</Label>
                    <Input v-model="form.name" type="text" placeholder="Name" />
                    <div class="text-sm text-red-500" v-if="form.errors.name"></div>
                </div>
                <div class="space-y-2">
                    <Label for="Product Price">Price</Label>
                    <Input v-model="form.price" type="number" placeholder="Price" />
                    <div class="text-sm text-red-500" v-if="form.errors.price"></div>
                </div>
                <div class="space-y-2">
                    <Label for="Product Description">Description</Label>
                    <Input v-model="form.description" type="text" placeholder="Description" />
                    <div class="text-sm text-red-500" v-if="form.errors.description"></div>
                </div>
                <Button type="submit">Add A Product</Button>
            </form>
        </div>
    </AppLayout>
</template>
