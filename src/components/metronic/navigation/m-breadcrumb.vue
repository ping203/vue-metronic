<template>
	<ul class="page-breadcrumb">
		<li :key="index" v-for="(page, index) in breadcrumbs">
			<router-link v-if="index != breadcrumbs.length - 1" :to="{ name: page.RouteName }">{{page.Title}}</router-link>
			<template v-else>
				{{page.Title}}
			</template>
		</li>
	</ul>
</template>

<script>
export default {
	name: "BreadCrumbComponent",
	computed: {
		breadcrumbs () {
			var breads = this.$route.matched.map(function (item) {
				return {
					Title: item.meta.title,
					RouteName: item.name
				}
			})

			if (this.$route.params.breadcrumb) {
				breads.push({
					title: this.$route.params.breadcrumb
				})
			}

			return breads
		}
	}
}
</script>
