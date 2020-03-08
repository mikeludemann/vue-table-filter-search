<template>
	<div class="home">
		<img alt="Vue logo" src="../assets/logo.png">
		<HelloWorld msg="Welcome to Your Vue.js App"/>
		<DynamicTableFilterSearch 
			:headlines='[{name: "First Name"}, {name: "Last Name"}, {name: "E-Mail"}, {name: "Birthday"}]' 
			:datas='[{firstname: "Sam", lastname: "Mueller",  email: "adam.mueller@live.com", birthday: "21-01-1980"}, {firstname: "Mary", lastname: "White", email: "m-white@icloud.com", birthday: "11-04-1978"}]'
			id="tableDataTwo"
			searchField="searchMainFilter"
		/>
		<!--<VisibleTableFilterSearch 
			:headlines='[{name: "First Name"}, {name: "Last Name"}, {name: "E-Mail"}, {name: "Birthday"}]' 
			:datas='[{firstname: "Adam", lastname: "Mueller",  email: "adam.mueller@live.com", birthday: "21-01-1980"}, {firstname: "Mary", lastname: "White", email: "m-white@icloud.com", birthday: "11-04-1978"}]'
			id="tableDataOne"
			searchField="searchMainFilter"
		/>-->
	</div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue';
import VisibleTableFilterSearch from '@/components/visible-table-filter-search.vue';
import DynamicTableFilterSearch from '@/components/dynamic-table-filter-search.vue';

export default {
	name: 'Home',
	components: {
		HelloWorld,
		VisibleTableFilterSearch,
		DynamicTableFilterSearch
	}
}
</script>
