<template lang="html">

	<section class="dynamic-table-filter-search">
		<div>
			<input type="text" :id="searchField"/>
			<table :id="id" :style="hiding">
				<tr>
					<th v-for="headline in headlines">{{headline.name}}</th>
				</tr>
				<tr v-for="data in datas">
					<td>{{data.firstname}}</td>
					<td>{{data.lastname}}</td>
					<td>{{data.email}}</td>
					<td>{{data.birthday}}</td>
				</tr>
			</table>
		</div>
	</section>

</template>

<script lang="js">

	export default {
		name: 'DynamicTableFilterSearch',
		props: {
			id: {
				type: String,
				required: true
			},
			searchField: {
				type: String,
				required: true
			},
			headlines: {
				type: Object,
				required: true
			},
			datas: {
				type: Object,
				required: true
			}
		},
		mounted () {
			this.insertExternalSource();
		},
		data () {
			return {
				tableHide: 'hiding'
			}
		},
		methods: {
			insertExternalSource: function(){
				var textfield = document.getElementById(this.searchField);
				var tableContainer = document.getElementById(this.id);

				function searchTable(textfield, container, row, column) {

					var search,
						filter, 
						found, 
						table, 
						rows, 
						columns, 
						i, 
						j;

					search = document.querySelector(textfield);
					filter = search.value.toUpperCase();
					table = document.querySelector(container);
					rows = table.querySelectorAll(row);

					for (i = 0; i < rows.length; i++) {

						columns = rows[i].querySelectorAll(column);

						if(i == 0){

							columns = table.rows.item(i).cells.length;
							continue;

						}

						for (j = 0; j < columns.length; j++) {

							if (columns[j].innerHTML.toUpperCase().indexOf(filter) > -1) {

								found = true;

							}

						}

						if (found) {

							tableContainer.style.display = "none";
							rows[i].style.display = "";

							found = false;

						} else {

							tableContainer.style.display = "";
							rows[i].style.display = "none";

						} 

					}

				}

				var txt = "#" + this.searchField;
				var tdata = "#" + this.id;

				textfield.addEventListener("keyup", function(){
					searchTable(txt, tdata, "tr", "td");
				});
			}
		},
		computed: {
			hiding: function(){
				return {
					display: "none"
				};
			}
		}
}


</script>

<style lang="scss">
	.dynamic-table-filter-search {
		color: red;
	}
</style>
