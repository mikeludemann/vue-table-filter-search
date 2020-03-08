<template lang="html">

	<section class="visible-table-filter-search">
		<div>
			<input type="text" :id="searchField"/>
			<table :id="id">
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
		name: 'VisibleTableFilterSearch',
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

			}
		},
		methods: {
			insertExternalSource: function(){
				var textfield = document.getElementById(this.searchField);
				var table = document.getElementById(this.id);

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

							rows[i].style.display = "";

							found = false;

						} else {

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

		}
}


</script>

<style scoped lang="scss">
	.visible-table-filter-search {

	}
</style>
