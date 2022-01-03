<template>
        <div class="ui container">
            <input v-model="filterBy" placeholder="Filter By Last Name">
            <table class="ui celled table">  
                <tr>
                    <th>Avatar</th>
                    <th @click="sortBy = 'firstName'">First Name</th>
                    <th @click="sortBy = 'lastName'">Last Name</th>
                    <th @click="sortBy = 'email'">Email</th>
                    <th @click="sortBy = 'phone'">Phone</th>
                    <th @click="sortBy = 'department'">Department</th>
                </tr>
                <tr v-for="(employee, index) in sortedEmployees" :key="index">  
                    <td><img :src="employee.photoUrl"></td>     <!-- v-bind -->
                    <td>{{ employee.firstName }}</td>    
                    <td>{{ employee.lastName }}</td>    
                    <td>{{ employee.email }}</td>    
                    <td>{{ employee.phone }}</td>    
                    <td>{{ employee.department }}</td>  
                </tr>
                <tr v-if="employees.length === 0">
                    <td colspan="6">No employees found</td>
                </tr>
            </table>
        </div>
</template>

 <script>
    export default {
        name: 'StaffDirectory,',
        data() {
            return {
                filterBy: "",
                sortBy: "department",  
                employees: [
                        {
                            "firstName": "amelia",
                            "lastName": "austin",
                            "photoUrl": "https://randomuser.me/api/portraits/thumb/women/9.jpg",
                            "email": "amelia.austin@example.com",
                            "phone": "(651)-507-3705",
                            "department": "Engineering"
                        },
                        {
                            "firstName": "bobbie",
                            "lastName": "murphy",
                            "photoUrl": "https://randomuser.me/api/portraits/thumb/women/79.jpg",
                            "email": "bobbie.murphy@example.com",
                            "phone": "(925)-667-7604",
                            "department": "Management"
                        },
                        {
                            "firstName": "kristin",
                            "lastName": "terry",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/women/45.jpg",
                            "email": "kristin.terry@example.com",
                            "phone": "(021)-544-1184",
                            "department": "Sales"
                        },
                        {
                            "firstName": "brandon",
                            "lastName": "griffin",
                            "photoUrl": "https://randomuser.me/api/portraits/thumb/men/59.jpg",
                            "email": "brandon.griffin@example.com",
                            "phone": "(509)-317-9506",
                            "department": "Management"
                        },
                        {
                            "firstName": "tammy",
                            "lastName": "gibson",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/women/72.jpg",
                            "email": "tammy.gibson@example.com",
                            "phone": "(815)-727-0663",
                            "department": "Support"
                        },
                        {
                            "firstName": "edward",
                            "lastName": "diaz",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/men/35.jpg",
                            "email": "edward.diaz@example.com",
                            "phone": "(164)-374-5203",
                            "department": "Support"
                        },
                        {
                            "firstName": "celina",
                            "lastName": "jackson",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/women/14.jpg",
                            "email": "celina.jackson@example.com",
                            "phone": "(358)-185-5629",
                            "department": "Management"
                        },
                        {
                            "firstName": "marion",
                            "lastName": "schmidt",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/men/20.jpg",
                            "email": "marion.schmidt@example.com",
                            "phone": "(048)-711-3842",
                            "department": "Support"
                        },
                        {
                            "firstName": "jackie",
                            "lastName": "fletcher",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/women/52.jpg",
                            "email": "jackie.fletcher@example.com",
                            "phone": "(325)-717-2960",
                            "department": "Engineering"
                        },
                        {
                            "firstName": "vickie",
                            "lastName": "jones",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/women/93.jpg",
                            "email": "jackie.fletcher@example.com",
                            "phone": "(017)-549-4725",
                            "department": "HR"
                        },
                        {
                            "firstName": "rosa",
                            "lastName": "rose",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/women/91.jpg",
                            "email": "rosa.rose@example.com",
                            "phone": "(994)-899-5188",
                            "department": "HR"
                        },
                        {
                            "firstName": "stacey",
                            "lastName": "reyes",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/women/91.jpg",
                            "email": "stacey.reyes@example.com",
                            "phone": "(934)-474-7495",
                            "department": "Engineering"
                        },
                        {
                            "firstName": "nevaeh",
                            "lastName": "phillips",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/women/6.jpg",
                            "email": "nevaeh.phillips@example.com",
                            "phone": "(500)-363-3829",
                            "department": "Engineering"
                        },
                        {
                            "firstName": "jeanette",
                            "lastName": "walters",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/women/68.jpg",
                            "email": "jeanette.walters@example.com",
                            "phone": "(229)-343-3330",
                            "department": "Engineering"
                        },
                        {
                            "firstName": "sara",
                            "lastName": "bell",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/women/29.jpg",
                            "email": "sara.bell@example.com",
                            "phone": "(607)-032-3021",
                            "department": "Engineering"
                        },
                        {
                            "firstName": "lester",
                            "lastName": "beck",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/men/33.jpg",
                            "email": "lester.beck@example.com",
                            "phone": "(331)-938-8441",
                            "department": "Management"
                        },
                        {
                            "firstName": "marion",
                            "lastName": "palmer",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/women/29.jpg",
                            "email": "marion.palmer@example.com",
                            "phone": "(968)-500-3203",
                            "department": "Sales"
                        },
                        {
                            "firstName": "penny",
                            "lastName": "chapman",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/women/84.jpg",
                            "email": "penny.chapman@example.com",
                            "phone": "(433)-799-1901",
                            "department": "Engineering"
                        },
                        {
                            "firstName": "albert",
                            "lastName": "mendoza",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/men/21.jpg",
                            "email": "albert.mendoza@example.com",
                            "phone": "(626)-787-6708",
                            "department": "Sales"
                        },
                        {
                            "firstName": "eugene",
                            "lastName": "alexander",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/men/81.jpg",
                            "email": "eugene.alexander@example.com",
                            "phone": "(965)-992-7966",
                            "department": "Sales"
                        },
                        {
                            "firstName": "brianna",
                            "lastName": "pena",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/women/8.jpg",
                            "email": "brianna.pena@example.com",
                            "phone": "(177)-577-2703",
                            "department": "Sales"
                        },
                        {
                            "firstName": "shane",
                            "lastName": "roberts",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/men/61.jpg",
                            "email": "shane.roberts@example.com",
                            "phone": "(578)-689-2670",
                            "department": "Management"
                        },
                        {
                            "firstName": "raul",
                            "lastName": "gilbert",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/men/95.jpg",
                            "email": "raul.gilbert@example.com",
                            "phone": "(513)-804-0780",
                            "department": "Support"
                        },
                        {
                            "firstName": "jennie",
                            "lastName": "rose",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/women/79.jpg",
                            "email": "jennie.rose@example.com",
                            "phone": "(346)-289-7297",
                            "department": "Sales"
                        },
                        {
                            "firstName": "richard",
                            "lastName": "simmons",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/men/26.jpg",
                            "email": "richard.simmons@example.com",
                            "phone": "(147)-650-9581",
                            "department": "Support"
                        },
                        {
                            "firstName": "alberto",
                            "lastName": "powell",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/men/41.jpg",
                            "email": "alberto.powell@example.com",
                            "phone": "(423)-042-1027",
                            "department": "Sales"
                        },
                        {
                            "firstName": "julia",
                            "lastName": "lawson",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/women/15.jpg",
                            "email": "julia.lawson@example.com",
                            "phone": "(316)-395-5276",
                            "department": "Sales"
                        },
                        {
                            "firstName": "edgar",
                            "lastName": "johnston",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/men/70.jpg",
                            "email": "edgar.johnston@example.com",
                            "phone": "(954)-827-7399",
                            "department": "Support"
                        },
                        {
                            "firstName": "allen",
                            "lastName": "baker",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/men/46.jpg",
                            "email": "allen.baker@example.com",
                            "phone": "(083)-648-3550",
                            "department": "Sales"
                        },
                        {
                            "firstName": "scott",
                            "lastName": "pena",
                            "photoUrl":
                                "https://randomuser.me/api/portraits/thumb/men/69.jpg",
                            "email": "scott.pena@example.com",
                            "phone": "(566)-201-1879",
                            "department": "Support"
                        }
                    ]
                };

        },
        computed: {
            sortedEmployees() {
                return this.employees.filter(employee => employee.lastName.includes(this.filterBy)
                ).sort(
                    (a, b) => a[this.sortBy].localeCompare(b[this.sortBy])
                );
            }
        }
    }
    </script>


<style>
    h1.ui.center.header {
        margin-top: 3em;
    }

    .ui.table th:not(:first-child):hover {
        cursor: pointer;
    }

    input {
        padding: 3px;
    }
</style>