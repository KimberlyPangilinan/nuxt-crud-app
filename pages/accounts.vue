

<template lang="">
    <main class="mt-[12em] w-100 min-h-screen flex flex-col px-16 gap-4">
<!-- search filters and buttons -->
        <div class="flex justify-between fixed top-20 left-0 px-16 w-screen bg-white">
            <div class="flex gap-4 py-8  ">
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
                <div class="border rounded-md max-w-fit flex justify-center flex-row-reverse ">
                    <input
                        class="py-2 px-4 placeholder:text-xs placeholder:text-slate-400 outline-none "
                        type="text"
                        id="department"
                        name="department"
                        placeholder="department"
                        v-model="filterDept"
                        />
                    <button class="bg-primary-red px-4 rounded-sm"><Icon class="text-white" icon="iconoir:filter" /></button>
                </div>
            </div>
            <div class="py-8">    
                 <button 
                    class="bg-primary-red text-white py-3 px-6 flex items-center gap-2 text-sm rounded"
                    @click="isOpen = !isOpen"
                    id="new"
                 ><Icon icon="ic:baseline-plus"/>New</button>
            </div>
        </div>
<!-- this is the new employee form-->
        <div v-if="isOpen"></div>
        <div v-else class="border-t-2 border-gray-100">
            <form action="" class="flex py-6">
                <div class="flex justify-center items-center w-[30%]">
                    <label for="image" class="flex flex-col justify-center items-center gap-4">
                        <img class="w-[7em] border-dashed border-gray-400 border-2" src="https://static.vecteezy.com/system/resources/thumbnails/002/058/031/small/picture-icon-photo-symbol-illustration-for-web-and-mobil-app-on-grey-background-free-vector.jpg"/>
                        <span class="text-[#00A2FD]">Upload image</span>
                        <input type="file" id="image" class="hidden"/>
                    </label>
                </div>
                <div class="w-[50%] flex flex-col gap-4">
                    <div class="flex gap-2">
                        <InputBox type="text" id="First Name" v-model="fName" />
                        <InputBox type="text" id="Middle Name" v-model="mName"/>
                        <InputBox type="text" id="Last Name" v-model="lName"/>
                    </div>
                    <div class="flex gap-2">
                        <InputBox type="email" id="Email" v-model="email"/>
                        <InputBox type="text" id="Department" v-model="department"/>
                        <InputBox type="text" id="ID No." v-model="id"/>
                    </div>
                    <div class="flex gap-2">
                        <input type="radio" id="active" name="isActive" checked value="Active" @click="isActive= true">
                        <label for="deactivated">Active</label>
                        <input type="radio" id="deactivated" name="isActive" value="Deactivated" @click="isActive= false">
                        <label for="deactivated">Deactivated</label>
                        
                    </div>
                </div>
                <div class="flex flex-col justify-center gap-2 w-[20%] px-12">
                    <VButton color="green" id="Add" @click="handleAddItem"/>
                    <VButton color="#D9D9D9" id="Cancel"/>
                </div>
            </form>
        </div>
<!-- table -->
<div class="flex gap-4">
  <div class="flex flex-col gap-6 grow">
    <h2 class="font-semibold flex w-[100%] items-center gap-10">
      Employees Account
      <hr class="grow bg-red-100 h-[0.3rem]">
    </h2>
    <div class="flex gap-4 items-start ">
      <table class="table-auto grow text-[#667085]  ">
        <thead>
          <tr class="text-left text-gray-500 font-medium text-xs h-16">
            <th class="p-3"><input type="checkbox"/></th>
            <th class="p-3">File Name/ID No.</th>
            <th class="p-3">Date</th>
            <th class="p-3">Email</th>
            <th class="p-3">Department</th>
            <th class="p-3">Active</th>
            <th></th>
          </tr>
        </thead>
        <tbody>
          <tr
            @click="() => handleRowClick(item)"
            v-for="item in filteredItemsByName"
            class="odd:bg-gray-100 text-gray-500 hover:bg-red-50"
          >
            <td class="p-3 bg-white"><input type="checkbox"/></td>
            <td class="flex gap-4 bg-white p-3 min-w-[300px]">
              <img :src="item.image" class="w-[47px]"/> 
              <h4 class="flex flex-col text-black">
                {{ item.fName }} {{ item.mName }} {{ item.lName }} 
                <span class="text-sm text-[#667085]">{{ item.id }}</span>
              </h4>
            </td>
            <td class="p-3">{{ item.date }}</td>
            <td class="p-3">{{ item.email }}</td>
            <td class="p-3">{{ item.department }} </td>
            <td class="p-3 font-semibold" :style="{ color: item.isActive ? 'green' : 'red' }">
              {{ item.isActive ? 'Active' : 'Deactivated' }}
            </td>
            <td></td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
  
  <div v-if="clickedRow" class="flex flex-col max-w-[380px] bg-[#F8F7F7] p-6 max-h-[70vh]">
    <div class="flex gap-1 justify-end">
        <button class="p-2 rounded-md bg-yellow-400" ><Icon class="text-white" icon="grommet-icons:power-reset" /></button>
        <button class="p-2 rounded-md bg-green-600" @click="isDisabled=!isDisabled"><Icon class="text-white" icon="gg:pen" /></button>
        <button class="p-2 rounded-md bg-red-600 " @click="() => handleDelete(clickedRow)"><Icon class="text-white" icon="ant-design:delete-outlined" /></button>
    </div>
    <div class="flex p-4 gap-4 items-center grow">
      <img :src="clickedRow.image" class="w-[99px] aspect-square object-cover"/>
      <div class="text-xs font-medium flex flex-col">
        <span class="text-[#00A2FD] ">Upload image</span>
        {{ clickedRow.fName }} {{ clickedRow.mName }} {{ clickedRow.lName }} 
      </div>
    </div>
    <div class="flex justify-between gap-4">
        <div class="flex flex-col gap-4">
            <div class="flex flex-col">
                <label class="text-xs">First Name</label>
                <input type="text" v-model="clickedRow.fName" :disabled="isDisabled" class="p-2 bg-[#F6F6F6] disabled:text-[#766E6E] text-xs rounded-md border  border-slate-300 placeholder-slate-400 focus:outline-none placeholder:text-slate-400" />
            </div>
            <div class="flex flex-col">
                <label class="text-xs">Middle</label>
                <input type="text" v-model="clickedRow.mName" :disabled="isDisabled" class="p-2 bg-[#F6F6F6] disabled:text-[#766E6E] text-xs rounded-md border  border-slate-300 placeholder-slate-400 focus:outline-none placeholder:text-slate-400" />
            </div>
            <div class="flex flex-col">
                <label class="text-xs">Last Name</label>
                <input type="text" v-model="clickedRow.lName" :disabled="isDisabled" class="p-2 bg-[#F6F6F6] disabled:text-[#766E6E] text-xs rounded-md border  border-slate-300 placeholder-slate-400 focus:outline-none placeholder:text-slate-400" />
            </div>
            
        </div>
        <div class="flex flex-col gap-4 ">
            <div class="flex flex-col">
                <label class="text-xs">Email</label>
                <input type="email" v-model="clickedRow.email" :disabled="isDisabled" class="p-2 bg-[#F6F6F6] disabled:text-[#766E6E] text-xs rounded-md border  border-slate-300 placeholder-slate-400 focus:outline-none placeholder:text-slate-400" />
            </div>
            <div class="flex flex-col">
                <label class="text-xs">Department</label>
                <input type="email" v-model="clickedRow.department" :disabled="isDisabled" class="p-2 bg-[#F6F6F6] disabled:text-[#766E6E] text-xs rounded-md border  border-slate-300 placeholder-slate-400 focus:outline-none placeholder:text-slate-400" />
            </div>
            <div class="flex flex-col">
                <label class="text-xs">ID No.</label>
                <input type="email" v-model="clickedRow.id" :disabled="isDisabled" class="p-2 bg-[#F6F6F6] disabled:text-[#766E6E] text-xs rounded-md border  border-slate-300 placeholder-slate-400 focus:outline-none placeholder:text-slate-400" />
            </div>
        </div>
      
    </div>
    <div class="pt-4 flex gap-2 justify-end grow align-bottom items-end">
        <button class="px-4 py-3 w-[80px] h-[46px] rounded-sm text-xs text-white bg-[#D9D9D9]" @click="handleCancel">Cancel</button>
        <button class="px-4 py-3 w-[80px] h-[46px] rounded-sm text-xs text-white bg-[#308F00]" @click="handleUpdate">Update</button>
    </div>
  </div>
</div>

    </main>
</template>


<script setup>

import { Icon } from '@iconify/vue';
import { ref ,computed } from 'vue'
import nuxtStorage from 'nuxt-storage';


 const items = ref([
    {
        image: 'https://media.istockphoto.com/id/1322275410/photo/profile-of-young-man.jpg?s=612x612&w=0&k=20&c=Ssbvdy81Z-SZfPvUyxS3sixqpdYIlB7bNQprGaSRSDc=',
        fName: 'Juan ',
        lName: 'Dela Cruz',
        id: '0009-2039-49',
        date:'Jan 4, 2021',
        email: 'juandelacruz@gmail.com',
        department: 'Accounting',
        isActive: true

    },
    { 
        image: 'https://images.unsplash.com/photo-1492562080023-ab3db95bfbce?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8Nnx8bWFsZSUyMHByb2ZpbGV8ZW58MHx8MHx8fDA%3D&auto=format&fit=crop&w=600&q=60',
        fName: 'Shaina',
        lName: 'De Guzman',
        id: '0009-2039-56',
        date:'Sep 12, 2019',
        email: 'shaina@gmail.com',
        department: 'IT',
        isActive: true

    },
    { 
        image: 'https://images.unsplash.com/photo-1535713875002-d1d0cf377fde?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxzZWFyY2h8NHx8bWFsZSUyMHByb2ZpbGV8ZW58MHx8MHx8fDA%3D&auto=format&fit=crop&w=600&q=60',
        fName: 'Michael Sy',
        lName: 'Sy',
        id: '0009-2039-49',
        date:'Feb 4, 2021',
        email: 'juandelacruz@gmail.com',
        department: 'juandelacruz@gmail.com',
        isActive: false

    },
   
])
const fName = ref('')
const mName = ref('')
const lName = ref('')
const email = ref('')
const department = ref('')
const name = ref('')
const isOpen = ref(true)
const searchText = ref("")
const filterDept = ref("")
const clickedRow=ref(null)
const isActive=ref(true)

const isDisabled=ref(true)
// Search by name
const filteredItemsByName = computed(() => {
    if (!searchText.value) {
        return items.value;
    }
    return items.value.filter((item) =>
        item.fName.toLowerCase().includes(searchText.value.toLowerCase())||
        item.lName.toLowerCase().includes(searchText.value.toLowerCase())
    );
});

// Function for handling row click
const handleRowClick = (item)=>{
    console.log("sf")
    console.log("Row clicked:", item.name, item.department);
    isOpen.value = true
    clickedRow.value = item
}


//using the nuxStorage for getting the saved data if available
const savedItems = nuxtStorage.localStorage.getData('employeeItems');
if (savedItems) {
    items.value = JSON.parse(savedItems);
}

//push an Item to the items array of objects and adding to local storage
const addItem = (newItem) => {
    items.value.push(newItem);
    nuxtStorage.localStorage.setData('employeeItems',JSON.stringify(items.value), 1, 'h');
};

const handleAddItem = () => {
    const newItem = {
        image: 'img',
        fName: fName,
        lName: lName,
        mName: mName,
        id: 100,
        date: new Date(),
        email: email,
        department: department,
        isActive: isActive,
    };

    addItem(newItem);
    clickedRow.value = null
    isOpen.value = !isOpen.value; 
};

const handleCancel = ()=> {
    clickedRow.value = null
}

const handleDelete = (item) => {
  const index = items.value.findIndex(emp => emp.id === item.id);
  if (index !== -1) {
    items.value.splice(index, 1);
    nuxtStorage.localStorage.setData('employeeItems', JSON.stringify(items.value), 1, 'h');
  }
  clickedRow.value = null;
};
const handleUpdate = ()=> {

}


</script>
