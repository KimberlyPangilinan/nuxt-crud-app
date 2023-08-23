

<template lang="">
    <main class="w-100 min-h-screen flex flex-col px-16 gap-4">
        <!-- search filters and buttons -->
        <div class="flex justify-between">
            <div class="flex gap-4 py-8">
                <div class="border rounded-sm max-w-fit py-2 px-4 flex justify-center ">
                <input
                    class="placeholder:text-xs placeholder:text-slate-400 outline-none "
                    type="text"
                    id="search"
                    name="search"
                    v-model="searchText"
                    placeholder="Search by name.."
                    />
                <button><Icon class="text-gray-400" icon="carbon:search" /></button>
                </div>
                <div class="border rounded-sm max-w-fit flex justify-center flex-row-reverse ">
                    <input
                        class="py-2 px-4 placeholder:text-xs placeholder:text-slate-400 "
                        type="text"
                        id="department"
                        name="department"
                        placeholder="department"
                        />
                    <button class="bg-primary-red px-4"><Icon class="text-white" icon="iconoir:filter" /></button>
                </div>
            </div>
            <div class="py-8">    
                 <button 
                    class="bg-primary-red text-white py-3 px-6 flex items-center gap-2 text-sm rounded"
                    @click="isOpen = !isOpen"
                    id="new"
                 >
                    <Icon icon="ic:baseline-plus" /> New
                </button>
            </div>
        </div>
        <div v-if="isOpen"></div>
<div v-else>
    <form action="" class="flex py-8">
        <div class="flex justify-center items-center w-[15%]">
            <label for="image">
                <img class="w-20" src="https://static.vecteezy.com/system/resources/thumbnails/002/058/031/small/picture-icon-photo-symbol-illustration-for-web-and-mobil-app-on-grey-background-free-vector.jpg"/>
                 Upload image
                <input type="file" id="image" class="hidden"/>
            </label>
        </div>
        <div class="w-[70%]">
            <div class="flex gap-4">
                <InputBox type="text" id="First Name"/>
                <InputBox type="text" id="Middle Name"/>
                <InputBox type="text" id="Last Name"/>
            </div>
            <div class="flex gap-4">
                <InputBox type="email" id="Email"/>
                <InputBox type="text" id="Department"/>
                <InputBox type="text" id="ID No."/>
            </div>
        </div>
        <div class="flex flex-col justify-center gap-2 w-[15%] px-12">
            <VButton color="green" id="Add"/>
            <VButton color="#D9D9D9" id="Cancel"/>
        </div>
    </form>
</div>
        <!-- table -->
        <div class="flex flex-col gap-6">
            <h2 class="font-semibold flex w-[100%] items-center gap-10">Employees Account <hr class="grow bg-red-100 h-2"></h2>
            <table class="table-fixed">
                <thead>
                    <tr class="text-left text-gray-500 font-medium text-xs h-16">
                    <th class="p-3">File Name/ID No.</th>
                    <th class="p-3">Date</th>
                    <th class="p-3">Email</th>
                    <th class="p-3">Department</th>
                    <th class="p-3">Active</th>
                    </tr>
                </thead>
                <tbody>
                    <tr v-for="item in items" class=" odd:bg-gray-100 text-gray-500 hover:bg-red-50">
                    <td class="flex gap-4 bg-white p-3 ">
                        <img :src="item.image" class="w-[47px]"/> 
                        <h4 class="flex flex-col text-black">
                            {{ item.name }} 
                            <span class="text-sm ">{{item.id}}</span>
                        </h4>
                    </td>
                    <td class="p-3">{{item.date}}</td>
                    <td class="p-3">{{item.email}}</td>
                    <td class="p-3">{{ item.department}} </td>
                    <td class="p-3 font-semibold" :style="{ color: item.isActive ? 'green' : 'red' }">{{ item.isActive? 'Active': 'Deactivated' }}</td>
                    </tr>
                </tbody>
            </table>

        </div>
    </main>
</template>
<script setup>
import { Icon } from '@iconify/vue';
import { ref } from 'vue'

const isOpen = ref(true)

const items = ref([
    {
        image: 'https://media.istockphoto.com/id/1322275410/photo/profile-of-young-man.jpg?s=612x612&w=0&k=20&c=Ssbvdy81Z-SZfPvUyxS3sixqpdYIlB7bNQprGaSRSDc=',
        name: 'Juan Dela Cruz',
        id: '0009-2039-49',
        date:'Jan 4, 2021',
        email: 'juandelacruz@gmail.com',
        department: 'Accounting',
        isActive: true

    },
    { 
        image: 'https://images.unsplash.com/photo-1492562080023-ab3db95bfbce?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Nnx8bWFsZSUyMHByb2ZpbGV8ZW58MHx8MHx8fDA%3D&auto=format&fit=crop&w=600&q=60',
        name: 'Shaina De Guzman',
        id: '0009-2039-56',
        date:'Sep 12, 2019',
        email: 'shaina@gmail.com',
        department: 'IT',
        isActive: true

    },
    { 
        image: 'https://images.unsplash.com/photo-1535713875002-d1d0cf377fde?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8NHx8bWFsZSUyMHByb2ZpbGV8ZW58MHx8MHx8fDA%3D&auto=format&fit=crop&w=600&q=60',
        name: 'Michael Sy',
        id: '0009-2039-49',
        date:'Feb 4, 2021',
        email: 'juandelacruz@gmail.com',
        department: 'juandelacruz@gmail.com',
        isActive: false

    },
   
])
</script>
