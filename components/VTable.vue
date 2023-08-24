<template lang="">
     <div class="flex flex-col gap-6">
            <h2 class="font-semibold flex w-[100%] items-center gap-10">Employees Account <hr class="grow bg-red-100 h-2"></h2>
            <div class="flex gap-4">
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
                    <tr @click="() => handleRowClick(item)" v-for="item in filteredItemsByName" class=" odd:bg-gray-100 text-gray-500 hover:bg-red-50">
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
            <div v-if="clickedRow" class="flex flex-col w-[40%] bg-[#F8F7F7] p-12 grow">
                {{ clickedRow.name}}
            </div>
            
            </div>

        </div>
</template>
<script>
export default {
    
}
</script>
<style lang="">
    
</style>