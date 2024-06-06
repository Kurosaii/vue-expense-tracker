<template>
    <h3>Add New Transaction</h3>

    <form id="form">
        <div class="form-control">
            <label for="title">Title</label>
            <input
                id="title"
                type="text"
                placeholder="Enter title..."
            />
        </div>

        <div class="form-control">
            <label for="amount">
                Amount<br />
                (negative - expense, positive - income)
            </label>
            <input
                id="amount"
                type="number"
                placeholder="Enter amount..."
            />
        </div>

        <button class="btn">Add Transaction</button>
    </form>
</template>