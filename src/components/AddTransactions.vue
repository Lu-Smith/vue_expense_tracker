<template>
     <h3 class="font-semibold mt-6 border-solid border-b-2 border-slate-300">Add new transaction</h3>
    <form id="form" >
        <div class="form-control">
            <label for="text">Income/Expense</label>
            <input type="text" id="text" placeholder="Enter text..."/>
        </div>
        <div class="form-control">
            <label 
            for="amount"
            class="font-semibold">
            Amount <br />(negative - expense, positive - income)
            </label>
            <input
            type="text"
            id="amount"
            placeholder="Enter amount..."/>
        </div>
        <button class="btn">Add transaction</button>
    </form>
</template>