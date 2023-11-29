<template>
     <h3 class="font-semibold mt-6 border-solid border-b-2 border-slate-300">Add new transaction</h3>
    <form id="form" class="flex items-start justify-center flex-col gap-2 w-full" >
        <div class="flex items-start justify-center flex-col gap-2 w-full">
            <label 
            for="text"
            class="font-semibold mt-2">
                Income/Expense
            </label>
            <input 
            type="text" 
            id="text" 
            placeholder="Enter text..."
            class="px-2 py-1 w-full"/>
        </div>
        <div class="flex items-start justify-center flex-col gap-2 w-full">
            <label 
            for="amount"
            class="font-semibold">
            Amount 
            </label>
            <input
            type="text"
            id="amount"
            placeholder="Enter amount..."
            class="px-2 py-1 w-full"/>
        </div>
        <button class="bg-purple-400 px-2 py-1">Add transaction</button>
    </form>
</template>