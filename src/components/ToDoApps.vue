<template>
    <div class="flex flex-col gap-3 p-6">
        <h1 class="font-bold">TODO APPS</h1>
        <div id="countTask" class="flex flex-wrap gap-3">
            <div class="border rounded-md p-3 text-center">
                <p class="text-sm">PENDING</p>
                <p class="font-bold">{{ tasks.length }}</p>
            </div>
            <div class="border bg-blue-500 rounded-md p-3 text-center text-white">
                <p class="text-sm">LOW PRIORITY</p>
                <p class="font-bold">{{ lowTask }}</p>
            </div>
            <div class="border bg-yellow-500 rounded-md p-3 text-center text-white">
                <p class="text-sm">MEDIUM PRIORITY</p>
                <p class="font-bold">{{ medTask }}</p>
            </div>
            <div class="border bg-red-500 rounded-md p-3 text-center text-white">
                <p class="text-sm">HIGH PRIORITY</p>
                <p class="font-bold">{{ highTask }}</p>
            </div>
        </div>
        <div id="input" class="border rounded-md p-6">
            <form class="flex gap-6 flex-wrap justify-center items-end">
                <div class="flex flex-col gap-2 items-start">
                    <label for="name">Name</label>
                    <input v-model="newTask.name" type="text" class="rounded">
                </div>
                <div class="flex flex-col gap-2 items-start">
                    <label for="priority">Priority</label>
                    <select v-model="newTask.priority" class="rounded">
                        <option value="High">High</option>
                        <option value="Medium">Medium</option>
                        <option value="Low">Low</option>
                    </select>
                </div>
                <button @click.prevent="addTask" class="py-2 px-4 bg-green-500 rounded text-white font-semibold">Save</button>
            </form>
        </div>
        <div id="status" class="grid grid-cols-2 gap-4">
            <div id="todo" class="flex flex-col gap-3">
                <p class="font-bold">TODO</p>
                <ul class="flex flex-col gap-3">
                    <li class="border p-3 rounded-md md:grid md:grid-cols-2 flex flex-col gap-2 shadow-md" v-for="task in tasks" :key="task.name">
                        <div class="grid grid-rows-2 gap-3">
                            <p class="font-semibold">{{  task.name }}</p>
                            <div class="flex gap-1 items-center">
                                <div :class="{
                                    'w-[10px] h-[10px] bg-red-500': task.priority === 'High',
                                    'w-[10px] h-[10px] bg-yellow-500': task.priority === 'Medium',
                                    'w-[10px] h-[10px] bg-blue-500': task.priority === 'Low',
                                    }" class="w-[10px] h-[10px] rounded"></div>
                                <p>{{ task.priority }}</p>
                            </div>
                        </div>
                        <div class="flex gap-2 text-white font-semibold md:justify-end md:items-end justify-center">
                            <button @click="deleteTask(task)" class="p-2 bg-red-600 rounded-md">Delete</button>
                            <button @click="completeTask(task)" class="p-2 bg-green-600 rounded-md">Done</button>
                        </div>
                    </li>
                </ul>
            </div>
            <div id="done" class="flex flex-col gap-3">
                <p class="font-bold">DONE</p>
                <li class="border p-3 rounded-md grid grid-rows-2 gap-3 shadow-md" v-for="task in dones" :key="task.name">
                    <p class="font-semibold">{{  task.name }}</p>
                    <div class="flex gap-1 items-center">
                        <div :class="{
                            'w-[10px] h-[10px] bg-red-500': task.priority === 'High',
                            'w-[10px] h-[10px] bg-yellow-500': task.priority === 'Medium',
                            'w-[10px] h-[10px] bg-blue-500': task.priority === 'Low',
                            }" class="w-[10px] h-[10px] bg-green-500 rounded"></div>
                        <p>{{ task.priority }}</p>
                    </div>                   
                </li>
            </div>
        </div>
    </div>
</template>

<script>
    export default {
        data () {
            return {
                tasks: [
                    {name: "FE Sync-Up", priority: "High"},
                    {name: "Bug Fixing", priority: "Medium"},
                    {name: "Daily Report", priority: "Low"},
                ],
                dones: [
                    {name: "UI Design", priority: "High"},
                ],
                newTask: {
                    name: "",
                    priority: ""
                }
            }
        },
        computed: {
            lowTask() {
                let count = 0;
                for (let i = 0; i < this.tasks.length; i++) {
                    if (this.tasks[i].priority === "Low") {
                        count += 1
                    }
                }
                return count
            },
            medTask() {
                let count = 0;
                for (let i = 0; i < this.tasks.length; i++) {
                    if (this.tasks[i].priority === "Medium") {
                        count += 1
                    }
                }
                return count
            },
            highTask() {
                let count = 0;
                for (let i = 0; i < this.tasks.length; i++) {
                    if (this.tasks[i].priority === "High") {
                        count += 1
                    }
                }
                return count
            }
        },
        methods: {
            addTask() {
                if (this.newTask.name.trim() && this.newTask.priority.trim()) {
                    this.tasks.push({ ...this.newTask });
                    this.newTask.name = "";
                    this.newTask.priority = "";
                }
            },
            completeTask(task) {
                this.dones.push(task);
                this.deleteTask(task);
            },
            deleteTask(task) {
                const index = this.tasks.indexOf(task);
                if (index !== -1) {
                    this.tasks.splice(index, 1);
                }
            }
        }
    }
</script>