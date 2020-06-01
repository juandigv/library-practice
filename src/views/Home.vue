<template>
    <div class="home">
        <span>Library Practice</span>
        <br>
        <br>
        <input v-model="name" placeholder="Search" />
        <select v-model="selectedOption">
                          <option>All</option>
                          <option>Books</option>
                          <option>Magazines</option>
                          <option>Newspapers</option>
                          <option>Others</option>
                        </select>
        <br>
        <br>
        <span>Library by Name</span>
       
        <table style="margin: 0px auto">
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
        <br>
        <br>
        <span>Library by Description</span>
      
        <table style="margin: 0px auto">
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
                    desc: "First book of the series",
                    category: "Books"
                },
                {
                    code: "np01",
                    name: "Newspaper Manhattan",
                    desc: "sad news",
                    category: "Newspapers"
                },
                {
                    code: "mz01",
                    name: "Funny Magazine",
                    desc: "haha funny word",
                    category: "Magazines"
                },
                {
                    code: "ot01",
                    name: "Kronorium",
                    desc: "Generic description",
                    category: "Others"
                }, {
                    code: "bk02",
                    name: "Book Two",
                    desc: "Second book of the series",
                    category: "Books"
                },
                {
                    code: "np02",
                    name: "Newspaper DC",
                    desc: "good news",
                    category: "Newspapers"
                },
                {
                    code: "mz02",
                    name: "Clay Magazine",
                    desc: "Clayman approved",
                    category: "Magazines"
                },
                {
                    code: "ot02",
                    name: "Bounty Hunter Guide",
                    desc: "Generic description",
                    category: "Others"
                }, {
                    code: "bk03",
                    name: "Book Three",
                    desc: "Third book in the series",
                    category: "Books"
                },
                {
                    code: "np03",
                    name: "Newspaper Reeves",
                    desc: "its just news",
                    category: "Newspapers"
                },
                {
                    code: "mz03",
                    name: "PC Magazine",
                    desc: "rgb",
                    category: "Magazines"
                },
                {
                    code: "ot03",
                    name: "Sacred Jedi Texts",
                    desc: "read them have you",
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

    }
};
</script>

