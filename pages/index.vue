
<template lang="">
    <main class="mt-[14em] w-100 h-[80vh] gap-4 grid place-items-center md:mt-[8em]">
        <div class="flex flex-col items-center">
        <h1 class="font-sans text-xl font-extrabold">Need something done? </h1>
        <hr class="bg-[#B09191] h-1 w-10 mt-4"/>
        </div>
       <div class="flex flex-col justify-between gap-[103px] px-[174px] md:flex-row">
        <TheCard 
        title="Post a Job" 
        pic="/img/job.png" 
        desc="Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
        />
        <TheCard 
        title="Pay safely" 
        pic="/img/pay.png" 
        desc="Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
        />
        <TheCard 
        title="Post a Job" 
        pic="/img/help.png" 
        desc="Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua."
        />
       </div>
    </main>
</template>