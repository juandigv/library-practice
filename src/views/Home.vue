<template>
    <div class="home">
        <span>Library Practice</span>
        <br />
        <br />
        <input v-model="name" placeholder="Search" />
        <select v-model="selectedOption">
          <option>All</option>
          <option>Books</option>
          <option>Magazines</option>
          <option>Newspapers</option>
          <option>Others</option>
        </select>
        <button @click="SearchbyName()">Search by Name</button>
        <button @click="SearchbyDescription()">Search by Description</button>
        <br />
        <br />
    
        <table>
            <thead>
                <tr>
                    <th>Code</th>
                    <th>Name</th>
                    <th>Description</th>
                    <th>Category</th>
                </tr>
            </thead>
            <tbody>
                <tr :key="item.code" v-for="item in filteredListName">
                    <td>{{item.code}}</td>
                    <td>{{item.name}}</td>
                    <td>{{item.desc}}</td>
                    <td>{{item.category}}</td>
                </tr>
            </tbody>
        </table>
    
    
        <table>
            <thead>
                <tr>
                    <th>Code</th>
                    <th>Name</th>
                    <th>Description</th>
                    <th>Category</th>
                </tr>
            </thead>
            <tbody>
                <tr :key="item.code" v-for="item in filteredListDesc">
                    <td>{{item.code}}</td>
                    <td>{{item.name}}</td>
                    <td>{{item.desc}}</td>
                    <td>{{item.category}}</td>
                </tr>
            </tbody>
        </table>
    
        <br>
        <br>
    
    
    </div>
</template>

<script>
export default {
    name: "Home",
    components: {},
    data() {
        return {
            selectedOption: "All",
            name: "",
            list: [{
                    code: "bk01",
                    name: "Book One",
                    desc: "Generic description",
                    category: "Books"
                },
                {
                    code: "np01",
                    name: "Newspaper Manhattan",
                    desc: "Generic description",
                    category: "Newspapers"
                },
                {
                    code: "mz01",
                    name: "Funny Magazine",
                    desc: "Generic description",
                    category: "Magazines"
                },
                {
                    code: "ot01",
                    name: "Kronorium",
                    desc: "Generic description",
                    category: "Others"
                }
            ]
        };
    },
    computed: {
        filteredListName() {
            const categoryList = this.selectedOption === "All" ?
                this.list :
                this.list.filter(item => item.category === this.selectedOption);
            return this.name === "" ?
                categoryList :
                categoryList.filter(item => item.name.includes(this.name))
        },
        filteredListDesc() {
            const categoryList = this.selectedOption === "All" ?
                this.list :
                this.list.filter(item => item.category === this.selectedOption);
            return this.name === "" ?
                categoryList :
                categoryList.filter(item => item.desc.includes(this.name))
        },

    },
    methods: {
        SearchbyName() {

        },
        SearchbyDescription() {

        }
    }
};
</script>

